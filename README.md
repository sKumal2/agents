# FitFindr

> ### 👋 Start here
>
> **New to this repo? Read [RUNNING.md](RUNNING.md) first** — setup, every
> command, and what to do when something breaks.
>
> Once `python test.py` passes:
>
> ```bash
> python app.py listings --full -n 6      # read the data (Milestone 1)
> python app.py fields                    # what you can filter on
> python app.py ask 'vintage graphic tee under $30'
> ```
>
> All three tools are stubs, so that last command will do nothing useful yet.
> That's the starting position.
>
> **The rest of this file is your submission.** Fill it in as you go.

---

<!-- ─────────────────────────────────────────────────────────────────────────
     HOW TO USE THIS FILE

     This is your submission. Fill each section in as you finish the milestone
     it belongs to — don't leave it all to the end.

     Unit 3 asks for the first five sections. Unit 4 adds the five below them.
     Leave the unit 4 sections alone until then; they're here so you know
     what's coming.

     Everything is pasted as TEXT. No screenshots, no images, no video links.
     A typed block of output gets full credit; a picture of the same output
     gets none.
     ───────────────────────────────────────────────────────────────────────── -->

<!-- ═══════════════════════ UNIT 3 — THE BUILD ═══════════════════════ -->

## What This Does

<!-- Three or four sentences: what a user asks for, and what they get back. -->



---

## Tool Inventory

<!-- Four lines per tool. This is worth 2 points and it's the single most
     common place students lose them.

     "Returns a list" earns NOTHING. The description has to say what is IN
     the list.

     The empty case isn't optional either — it's the thing your loop branches
     on, and if you don't decide it here you'll discover it as a crash in
     Milestone 5. -->

### `search_listings`

- **What it does:**
<!-- This searches for all the listing that is available and returns matches. -->
**Inputs:** 
<!-- 'description' (str), 'size' (str), 'max_price' (float) -->
- **Returns:** 
<!-- A list of matching listing dicts, best match first, each with title, price, size, platform. -->
- **When it has nothing:**
<!-- When it has nothing that matches the user request, it returns an empty list, not None, and definitely not an exception. -->

### `suggest_outfit`

- **What it does:**
<!-- It takes an item and wardrobe, and returns outfit ideas.  -->
- **Inputs:**
'new_item' (dict), 'wardrobe' (dict)
- **Returns:**
It returns a string with outfit suggestions using the new item from the users wardrobe.
- **When it has nothing:**
It returns an empty string.


### `create_fit_card`

- **What it does:**
 It creates a short, shareable fashion caption based on the selected clothing item and the suggested outfit.
- **Inputs:**
new_item (dict) with details like title (str), price (float), size (str), and platform (str) and outfit_suggestion (str)
- **Returns:**
A string (str) containing a formatted fit card with the selected item's details, outfit suggestion, and a short description suitable for sharing.
- **When it has nothing:**
 Returns an empty string ("") if the item or outfit suggestion is missing or invalid.
---

## Planning Loop

<!-- Your branch rule, stated as a rule — the condition AND both paths — plus
     the file and function that holds it.

     Like this:
       "If search_listings returns an empty list, put a message in the session
        and stop. Otherwise take the first result and go to suggest_outfit."
        — agent.py::run_agent

     The grader checks your code against what you claim here, so the file and
     function have to be real. -->

**Branch rule:**
If search_listings returns an empty list ([]), add a message to the session saying no matching clothing items were found and stop the agent. Otherwise, select the first listing, pass it to suggest_outfit with the user's wardrobe, and pass the resulting outfit suggestion and selected listing to create_fit_card.

**Where it lives:** 
`agent.py::run_agent`
**How the query is parsed:** <!-- regex, string splitting, or asking the model — say which -->
The user's natural language query is parsed using regular expressions (regex) and string matching to extract clothing descriptions, size, and maximum price. For example, "vintage graphic tee size M under $30" is converted into description="vintage graphic tee", size="M", and max_price=30.0, which are passed to search_listings.

**What moves through the session:** <!-- which fields, in what order -->
 The session stores the user's original query, the parsed clothing description, size, and maximum price. The query is passed to search_listings, which returns matching listings. The first matching listing (new_item) is passed to suggest_outfit along with the user's wardrobe. The resulting outfit suggestion (outfit) and selected listing (new_item) are then passed to create_fit_card, which generates the final fit card returned to the user. If no listings are found, the session stores a message explaining that no matches were found, and the agent stops.
---

## Sample Run

<!-- Two things go here.

     1. One FULL query and its output, pasted as text.
     2. Your three per-tool terminal tests — the command and what it printed. -->

(.venv) samirkumal@MacBookAir agents % python app.py ask 'vintage graphic tee under $30'

  The planning loop isn't built yet — see the TODO in agent.py.

0 model calls this session

**One full query**

```
$ python app.py ask '...'

```

**The three tools, tested one at a time**

```
$ python -c "from tools import search_listings; print(search_listings('graphic tee', max_price=30))"

```
[{'id': 'lst_002', 'title': 'Y2K Baby Tee — Butterfly Print', 'description': 'Super cute early 2000s baby tee with butterfly graphic. Fitted crop length. Tag says medium but fits like a small.', 'category': 'tops', 'style_tags': ['y2k', 'vintage', 'graphic tee', 'cottagecore'], 'size': 'S/M', 'condition': 'excellent', 'price': 18.0, 'colors': ['white', 'pink', 'purple'], 'brand': None, 'platform': 'depop'}, {'id': 'lst_006', 'title': 'Graphic Tee — 2003 Tour Bootleg Style', 'description': 'Vintage-style bootleg tee with faded graphic. Slightly boxy fit. 100% cotton, soft and worn-in.', 'category': 'tops', 'style_tags': ['graphic tee', 'vintage', 'grunge', 'streetwear', 'band tee'], 'size': 'L', 'condition': 'good', 'price': 24.0, 'colors': ['black'], 'brand': None, 'platform': 'depop'}, {'id': 'lst_017', 'title': 'Mesh Long-Sleeve Top — Black', 'description': 'Sheer black mesh long-sleeve. Great for layering under a graphic tee or over a bralette. Stretchy material, fits true to size.', 'category': 'tops', 'style_tags': ['y2k', 'grunge', 'goth', 'layering'], 'size': 'S/M', 'condition': 'excellent', 'price': 15.0, 'colors': ['black'], 'brand': None, 'platform': 'depop'}, {'id': 'lst_033', 'title': 'Vintage Band Tee — Faded Grey', 'description': 'Faded grey band-style tee with distressed graphic. Crew neck. Fits boxy. Well-loved but no holes or major damage.', 'category': 'tops', 'style_tags': ['vintage', 'grunge', 'band tee', 'graphic tee','streetwear'], 'size': 'L', 'condition': 'fair', 'price': 19.0, 'colors': ['grey', 'charcoal'], 'brand': None, 'platform': 'depop'}, {'id': 'lst_011', 'title': 'Low-Rise Cargo Pants — Khaki', 'description': 'Y2K era low-rise cargo pants. Lots of pockets. Khaki color, slightly distressed at the hems. Great for layering with a long tee.', 'category': 'bottoms', 'style_tags': ['y2k', 'cargo', '2000s', 'streetwear'], 'size': 'W29', 'condition': 'fair', 'price': 27.0, 'colors': ['khaki', 'tan'], 'brand': None, 'platform': 'poshmark'}, {'id': 'lst_015', 'title': 'Vintage Graphic Hoodie — Faded Black', 'description': 'Faded black pullover hoodie with barely-visible vintage graphic on the chest. Cozy interior. Some pilling but adds to the worn-in look.', 'category': 'tops', 'style_tags': ['vintage', 'grunge', 'graphic', 'streetwear'], 'size': 'L', 'condition': 'fair', 'price': 26.0, 'colors': ['black', 'charcoal'], 'brand': None, 'platform': 'depop'}]
```
$ python -c "from tools import suggest_outfit; from utils.data_loader import load_listings, get_example_wardrobe; print(suggest_outfit(load_listings()[0], get_example_wardrobe()))"

```
Hey! Those vintage Levi's 501s are a total wardrobe staple and well worth grabbing for $38. Since you already own some great basics and streetwear pieces, here are two easy, completeoutfits you can make right away:

### Outfit 1: Effortless Streetwear
* **New Item:** Vintage Levi's 501 Jeans — Medium Wash
* **Top:** White ribbed tank top
* **Outerwear:** Vintage black denim jacket
* **Shoes:** Chunky white sneakers
* **Accessories:** Black crossbody bag

**Why it works:** The fitted white tank balances out the classic straight-leg cut of the 501s, while throwing the slightly cropped black denim jacket on top gives you that cool, effortless texture-on-texture look. Finish it off with your chunky white sneakers and black crossbody for an easy, everyday fit.

---

### Outfit 2: Cozy & Casual 
* **New Item:** Vintage Levi's 501 Jeans — Medium Wash
* **Top:** Oversized grey crewneck sweatshirt
* **Shoes:** Black combat boots
* **Accessories:** Brown leather belt

**Why it works:** The contrast between the super oversized grey crewneck and the structured, medium-wash denim is a classic styling trick. Tuck the front of the crewneck in just a bit to show off your brown leather belt, and anchor the outfit with your black combat boots to add a little edge to the cozy top.
```


$ python -c "from tools import create_fit_card; from utils.data_loader import load_listings; print(create_fit_card('jeans and white sneakers', load_listings()[0]))"

```
Nothing beats the effortless cool of Vintage Levi's 501 Jeans in Medium Wash. Throw them on with crisp white sneakers for that timeless, laid-back weekend look we're all chasing. Grab this pair right now on Depop for just $38.00 before someone else snags them.
```

Edge cases:
(.venv) samirkumal@MacBookAir agents % python -c "from tools import search_listings; print(search_listings('nonexistentxyz123'))"
[]
(.venv) samirkumal@MacBookAir agents % python -c "from tools import suggest_outfit; from utils.data_loader import load_listings, get_empty_wardrobe; print(suggest_outfit(load_listings()[0], get_empty_wardrobe()))"
These vintage Levi's 501s are an absolute wardrobe staple. Here are two easy ways to style them:

**1. Casual & Effortless (Everyday Wear)**
*   **Top:** A crisp, tucked-in white t-shirt or a relaxed-fit grey crewneck sweatshirt.
*   **Footwear:** Classic white leather sneakers (like Adidas Stan Smiths or Converse).
*   **Accessories:** A simple brown leather belt to pull the look together.

**2. Elevated & Cool (Night Out or Smart-Casual)**
*   **Top:** A black ribbed tank top layered under an oversized black blazer.
*   **Footwear:** Black leather ankle boots or loafers.
*   **Accessories:** A chunky silver chain necklace and a black leather shoulder bag. 

Both looks lean into the vintage, effortless vibe of the jeans while keeping things versatile and timeless!
---

python -c "from tools import create_fit_card; from utils.data_loader import load_listings; import config; config.CACHE_ENABLED=False; config.TEMPERATURE=0.9; item=load_listings()[0]; [print(f'\nRun {i+1}: {create_fit_card(\"Black jeans and white sneakers\", item)}') for i in range(3)]"


--- Run 1 ---
Nothing beats the effortless cool of these Vintage Levi's 501 Jeans in a medium wash. I love styling them with a basic black top and fresh white sneakers for that ultimate off-duty look. Grab them over on my Depop for just $38.00 before someone else does!

--- Run 2 ---
Nothing beats the effortless cool of a classic pair of Vintage Levi's 501 Jeans in a medium wash. Style them with a simple black tee and crisp white sneakers for that perfect off-duty look. Grab this timeless piece over on Depop for just $38.00 before someone else does!

--- Run 3 ---
Nothing beats a classic pair of Vintage Levi's 501 Jeans in a medium wash. Grab these on Depop right now for just $38.00. Throw them on with black jeans and white sneakers for an effortlessly cool, go-to everyday look.

## How I Used AI

<!-- Two specific moments. What you asked, what came back, what you changed.

     "I used Claude to help me code" is not enough.

     "I gave Claude my search_listings spec. It returned None on no match
     instead of an empty list, so I changed it" is the level we want. -->

**Moment 1**

- *What I asked for:*
I asked ChatGPT to help me implement the search_listings function using the existing load_listings() function, filtering by clothing description, size, and maximum price.

- *What came back:*
AI suggested using keyword overlap to rank matching listings, along with price and size filtering. It also suggested using regular expressions to prevent incorrect size matches, such as matching "L" with "XL".

- *What I changed:*
 I added the search logic to tools.py and tested it with different clothing descriptions and price limits. I made sure the function returned an empty list ([]) when no listings matched, as required by my tool specification.



**Moment 2**

- *What I asked for:*
I asked ChatGPT to help implement suggest_outfit and create_fit_card using the project's existing generate() model adapter.

- *What came back:*
AI provided prompts for generating outfit combinations based on the user's wardrobe and creating short, shareable fashion captions. It also included handling for empty wardrobes and missing outfit suggestions.

- *What I changed:*
I integrated the suggested implementations into tools.py, kept the existing function signatures, and tested the tools independently. I also included handling for empty inputs so the tools would return descriptive responses instead of failing.

<!-- ═══════════════════════ UNIT 4 — THE TEST ═══════════════════════

     Don't fill these in during unit 3.
     ═══════════════════════════════════════════════════════════════════ -->

---

## Run Log — Before

<!-- Five criteria, five tries each, in this exact format.

     Five, because your criteria are written out of five. Mark each try PASS
     or FAIL, count the passes, and read that count against your target — a
     row targeting 4 of 5 with three PASS cells is MISSED (3/5).

     `python run_eval.py --label before` runs everything and writes the table
     into results/. Paste it here and fill in the verdicts. -->

| Criterion | Target | Try 1 | Try 2 | Try 3 | Try 4 | Try 5 | Verdict |
|---|---|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |  |  |
| 2.  |  |  |  |  |  |  |  |
| 3.  |  |  |  |  |  |  |  |
| 4.  |  |  |  |  |  |  |  |
| 5.  |  |  |  |  |  |  |  |

**Real output from one try**, pasted as text, naming the file and function
that produced it:

```

```

---

## Verdicts and Diagnoses

<!-- MET or MISSED per criterion against LAST UNIT's target, plus a sentence on
     how you decided.

     Then, for every miss: which of the four places it happened — a tool, the
     loop's branch, the session, or the model's output — AND the mechanism.

     Not a diagnosis:  "The fit card was bad."
     A diagnosis:      "The fit card criterion missed on 2 of 5 items. Both had
                        an empty brand field. My prompt puts the brand in the
                        first sentence, so the card opened with a blank and read
                        like a fragment. The tool worked; the prompt assumed a
                        field that isn't always there."

     Look for a pattern. Three misses on the same tool is one problem, not
     three. -->

| # | Criterion | Target | Verdict | How I decided |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |
| 4 |  |  |  |  |
| 5 |  |  |  |  |

**Diagnoses**



---

## Loop Trace

<!-- One full run, printed step by step, with the MCP call visible in it.

     `python app.py ask '...' --trace` once you've added the trace.step()
     calls in Milestone 2.

     Worth pasting BOTH the happy path and the empty-search path. The empty
     one should be visibly shorter, because it stops. If your two traces are
     the same length, your branch isn't working — and this is the fastest way
     anyone will ever find that out. -->

**Happy path**

```

```

**Empty search**

```

```

**On the MCP move:** <!-- what changed in your code, and whether anything
behaved differently afterwards. If the rewire didn't work, say exactly where it
broke — the error text and the last thing that worked. That earns the point in
full. -->



---

## The Improvement

<!-- What you changed, why your diagnosis pointed at it, and the after-run in
     the same table format. One change, measured properly.

     `python run_eval.py --label after` -->

**What I changed:**

**Which failure it was meant to fix:**

### Run Log — After

| Criterion | Target | Try 1 | Try 2 | Try 3 | Try 4 | Try 5 | Verdict |
|---|---|---|---|---|---|---|---|
| 1.  |  |  |  |  |  |  |  |
| 2.  |  |  |  |  |  |  |  |
| 3.  |  |  |  |  |  |  |  |
| 4.  |  |  |  |  |  |  |  |
| 5.  |  |  |  |  |  |  |  |

**Did it help, and how do I know:**

<!-- If it made things worse, say that. Honestly reported, that earns full
     credit and is more interesting than one that worked. -->



---

## What's Still Broken

<!-- For each criterion still missed: what you'd do, and why you stopped where
     you did. "I ran out of time" is fine if it's true. Pretending nothing is
     left is not. -->



<!-- ═════════════════════════════════════════════════════════════════════

     SUBMISSION CHECKLIST — unit 3

       [ ] criteria.md has five numbered criteria, each with a target
       [ ] Each criterion has a reason underneath it
       [ ] All five unit 3 sections above have real content
       [ ] Tool Inventory: all three tools, inputs WITH TYPES, a specific
           return value, and the empty case
       [ ] Planning Loop names the branch rule and agent.py::run_agent
       [ ] Sample Run: one full query plus the three per-tool tests, as text
       [ ] At least four new commits
       [ ] Repository URL submitted — WRITE IT DOWN, you submit the same one
           next unit

     SUBMISSION CHECKLIST — unit 4

       [ ] mcp_server.py exists with one tool registered
           (or a written record of exactly where the rewire broke)
       [ ] Run Log — Before, five criteria, five tries each
       [ ] Real output pasted underneath, naming file and function
       [ ] A verdict on every criterion
       [ ] A diagnosis for every miss, naming a place AND a mechanism
       [ ] Loop Trace, with the MCP call visible in it
       [ ] All three failure modes triggered and handled
       [ ] One improvement, with Run Log — After in the same format
       [ ] What's Still Broken
       [ ] At least four new commits
       [ ] The SAME repository URL as last unit

     Do not delete and recreate this repository. Your commit history is what
     shows your criteria existed before your results did.
     ═════════════════════════════════════════════════════════════════════ -->

---

📖 **How to run this project: [RUNNING.md](RUNNING.md)**

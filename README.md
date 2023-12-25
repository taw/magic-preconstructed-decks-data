This repository contains machine readable decklist data generated from:

* https://github.com/taw/magic-preconstructed-decks
* https://github.com/taw/magic-search-engine

### Files

`decks.json` has traditional cards + sideboard structure, with all extra sections reusing sideboard.

`decks_v2.json` has cards + sideboard + commander + displayCommander + planarDeck + schemeDeck structure. You should use this one.

### Data format

Data file i a JSON array, with every element representing one deck.

Fields for each deck:

* name - deck name
* type - deck type
* set_code - mtgjson set code
* set_name - set name
* release_date - deck release date (many decks are released much after their set)
* cards - list of cards in the deck's mainboard
* sideboard - list of cards in the deck's sideboard
* commander - any commanders deck has (can be multiple for partners)
* displayCommander - non-playable (usually oversized) commander card
* planarDeck - planar deck for Planechase and Commander Planechase
* schemeDeck - scheme deck for Archenemy

Each card is:

* name - card name
* set_code - mtgjson set card is from (decks often have cards from multiple sets)
* number - card collector number
* foil - is this a foil version
* count - how many of given card
* mtgjson_uuid - mtgjson uuid
* multiverseid - Gatherer multiverseid of card if cards is on Gatherer (optional field)

### Data Limitations

All precons ever released by Wizards of the Coast should be present, and decklists should always contain right cards, with correct number and foiling, and mainboard/sideboard/commander status.

Source decklists generally do not say which printing (set and card number) each card is from, so we need to use heuristics to figure that out.

We use a script to infer most likely set for each card based on some heuristics, and as far as I know, it always matches perfectly.

That just leaves situation where there are multiple printings of same card in same set.

If some of the printings are special (full art basics, Jumpstart basics, showcase frames etc.), these have been manually chosen to match every product.

If you see any errors for anything mentioned above, please report them, so they can be fixed.

That just leaves the case of multiple non-special printings of same card in same set - most commonly basic lands.
In such case one of them is chosen arbitrarily, even though in reality a core set deck with 16 Forests would likely have 4 of each Forest in that core set, not 16 of one of them.

Feel free to create issue with data on exact priting if you want, but realistically we'll never get them all, and it's not something most people care about much.

---
title: "Dictionary German"
date: 2006-09-07
forum: Desktop Environments
---

### Post by Flavian on 2006-09-07
Hi folks.
I guess all of you know the nice "Dictionary" program, in "Applications" - "Accessoires"
My mother tongue is German so I was wondering if I could have German Dictionaries in there?

There is "English" - "French" and "Spanish" by default.
Would be really cool if someone could help me setting up a German dictionary.
Thanks!
Flo

---

### Post by Flavian on 2006-09-10
Can anyone please help me ?
I didn't find anything via google nor in the Forum...
Thanks for any help!
Flo

---

### Post by Kingsley on 2006-09-10
try looking in synaptic packet manager. it probably has a dictionary-de file.

---

### Post by domm on 2006-10-10
You can use the online databases of dict.org together with the gnome dictionary-tool-
In your case you'd  use the "eng-deu" database from dict.org.
Just go add a source and for server use "dict.org" and database "eng-deu".

You can query all available databases (you need to have the package "dict" installed) ba typing the following in a terminal:
```
dict -h dict.org --dbs

```

greetings
Domm

Edit: May I add that this does not only apply for german/english users. Let me just attach the list of databases available at dict.org:

```

 gcide      The Collaborative International Dictionary of English v.0.48
 wn         WordNet (r) 2.0
 moby-thes  Moby Thesaurus II by Grady Ward, 1.0
 elements   Elements database 20001107
 vera       Virtual Entity of Relevant Acronyms (Version 1.9, June 2002)
 jargon     Jargon File (4.3.1, 29 Jun 2001)
 foldoc     The Free On-line Dictionary of Computing (27 SEP 03)
 easton     Easton's 1897 Bible Dictionary
 hitchcock  Hitchcock's Bible Names Dictionary (late 1800's)
 bouvier    Bouvier's Law Dictionary, Revised 6th Ed (1856)
 devils     THE DEVIL'S DICTIONARY ((C)1911 Released April 15 1993)
 world02    CIA World Factbook 2002
 gazetteer  U.S. Gazetteer (1990)
 gaz-county U.S. Gazetteer Counties (2000)
 gaz-place  U.S. Gazetteer Places (2000)
 gaz-zip    U.S. Gazetteer Zip Code Tabulation Areas (2000)
 afr-deu    Africaan-German Freedict dictionary
 afr-eng    Africaan-English Freedict Dictionary
 ara-eng    English-Arabic Freedict Dictionary
 cro-eng    Croatian-English Freedict Dictionary
 cze-eng    Czech-English Freedict dictionary
 dan-eng    Danish-English Freedict dictionary
 deu-eng    German-English Freedict dictionary
 deu-fra    German-French Freedict dictionary
 deu-ita    German-Italian Freedict dictionary
 deu-nld    German-Nederland Freedict dictionary
 deu-por    German-Portugese Freedict dictionary
 eng-afr    English-Africaan Freedict Dictionary
 eng-ara    English-Arabic FreeDict Dictionary
 eng-cro    English-Croatian Freedict Dictionary
 eng-cze    English-Czech fdicts/FreeDict Dictionary
 eng-deu    English-German Freedict dictionary
 eng-fra    English-French Freedict Dictionary
 eng-hin    English-Hindi Freedict Dictionary
 eng-hun    English-Hungarian Freedict Dictionary
 eng-iri    English-Irish Freedict dictionary
 eng-ita    English-Italian Freedict dictionary
 eng-lat    English-Latin Freedict dictionary
 eng-nld    English-Netherlands Freedict dictionary
 eng-por    English-Portugese Freedict dictionary
 eng-rom    English-Romanian FreeDict dictionary
 eng-rus    English-Russian Freedict dictionary
 eng-spa    English-Spanish Freedict dictionary
 eng-swa    English-Swahili xFried/FreeDict Dictionary
 eng-swe    English-Swedish Freedict dictionary
 eng-tur    English-Turkish FreeDict Dictionary
 eng-wel    English-Welsh Freedict dictionary
 fra-deu    French-German Freedict dictionary
 fra-eng    French-English Freedict dictionary
 fra-nld    French-Nederlands Freedict dictionary
 hin-eng    English-Hindi Freedict Dictionary [reverse index]
 hun-eng    Hungarian-English FreeDict Dictionary
 iri-eng    Irish-English Freedict dictionary
 ita-deu    Italian-German Freedict dictionary
 jpn-deu    Japanese-German Freedict dictionary
 kha-deu    Khasi-German FreeDict Dictionary
 lat-deu    Latin-German Freedict dictionary
 lat-eng    Latin-English Freedict dictionary
 nld-deu    Nederlands-German Freedict dictionary
 nld-eng    Nederlands-English Freedict dictionary
 nld-fra    Nederlands-French Freedict dictionary
 por-deu    Portugese-German Freedict dictionary
 por-eng    Portugese-English Freedict dictionary
 sco-deu    Scottish-German Freedict dictionary
 scr-eng    Serbo-Croat-English Freedict dictionary
 slo-eng    Slovenian-English Freedict dictionary
 spa-eng    Spanish-English Freedict dictionary
 swa-eng    Swahili-English xFried/FreeDict Dictionary
 swe-eng    Swedish-English Freedict dictionary
 tur-deu    Turkish-German Freedict dictionary
 tur-eng    Turkish-English Freedict dictionary
 english    English Monolingual Dictionaries
 trans      Translating Dictionaries
 all        All Dictionaries (English-Only and Translating)
 web1913    Webster's Revised Unabridged Dictionary (1913)
 world95    The CIA World Factbook (1995)

```

---

### Post by domm on 2006-10-10
Another quick note. You can also use fuzzy search patterns instead of exact search to make it easier for people like me who are easily misspelling something;)

when you add a source in gnome-dict preferences you can specify a search-strategy in the field at the button. (in the german version it's called "Methode"). Ther you can enter any strategy your server supports.
Youn can find these out by typing the following in a terminal 
```

dict -h <server> -S

```

For "dict.org" you would get:
```

Strategies available:
 exact      Match headwords exactly
 prefix     Match prefixes
 substring  Match substring occurring anywhere in a headword
 suffix     Match suffixes
 re         POSIX 1003.2 (modern) regular expressions
 regexp     Old (basic) regular expressions
 soundex    Match using SOUNDEX algorithm
 lev        Match headwords within Levenshtein distance one
 word       Match separate words within headwords

```

You can also change the default search strategy in gconf:
apps=>gnome-dictionary=>strategy (default is exact)

---

### Post by domm on 2006-10-10
Yeaha, I'm posting like mad now.. save me

I found out that at "la-sorciere.de"  lives a dict server with a somewhat more appealing "deu-eng" resp. "eng-deu" database.

BTW: one can compare databases (i.e. there sizes by 
```
dict -h <server> -I 
```

---


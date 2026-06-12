---
title: "Linguists Unite!"
date: 2007-01-31
forum: Education &amp; Science
---

### Post by ushaba on 2007-01-31
I am a little curious if anyone has figured out how to use either IPA or the American Phonetic System to write in Ubuntu. IPA is preferred, but both will be useful at some time or another. Most searches on Google turn up meaningless acronyms. It's being remarkably unhelpful this time, actually... But it'd be especially cool if I could input IPA symbols via scim, as I am a Chinese/English user, making scim necessary. If I can't get IPA, how do I at least make the c with a carat over it, or the s with a carat over it (indicating the affricate ch and retroflex sh respectively)? I think czech uses both of those symbols, but not speaking Czech, this is all guesswork...

---

### Post by Toufik on 2007-02-02
First link in Google (search : phonetic ubuntu)

[http://packages.ubuntulinux.org/edgy/x11/xfonts-intl-phonetic](http://packages.ubuntulinux.org/edgy/x11/xfonts-intl-phonetic)

---

### Post by BLTicklemonster on 2007-02-02
Linguists Untie!!!

---

### Post by ushaba on 2007-02-03
maybe i'm just not very good at using google. i was searching for "fonts IPA scim" and then broadening it to "IPA linux" with a few other things. just imagining all of the time that could be saved if my brain were logical...

---

### Post by eggdeng on 2007-03-02
Be interested to hear if you managed to get the phonetics font working & if so, how?

---

### Post by WW on 2007-03-02
It looks like that IPA package is what you want, but in case you are still interested in just typing something like â: select the menu item System->Preferences->Keyboard, click on the "Layout Options" tab, and click on the "Compose key position".  Check one of the options to be your "compose-key". (I use "Right Win-key" for mine.)  Once you have chosen a compose-key, you can type â by hitting the key sequence <compose>^a (that's three keys: first the compose key, then the caret, then the a).  Similarly, <compose>~n results in ñ, <compose>"o results in ö, etc.

---

### Post by eggdeng on 2007-03-07
Maybe I'm just the last to find out, but after a few hours of usless googling and other pointless footering, it slowly dawned that ubuntu has IPA already enabled by default. In OpenOffice, it's just a question of going to the Insert menu, choosing Special character and then the font Gentium. Most of the IPA glyphs are in the IPA Extensions section but some are in Latin Extended-A, see attached screenshot. 
I'm not sure if the original poster was looking for a keyboard manager (like Keyman in W**nd*ws)  to help input the characters, though personally, I always found Keyman a chore & not really worth the hassle.

---

### Post by dhelm on 2007-03-08
I'm a new linux user, but on windows I'd always use the S.I.L. fonts (usually Doulous): [http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=DoulosSIL_download#1fd0063a](http://scripts.sil.org/cms/scripts/page.php?site_id=nrsi&item_id=DoulosSIL_download#1fd0063a)

I had a great layout that someone had pieced together for MS, but I can't find one yet for Ubuntu. I'll post with any success I might have, but I might just write my own. If any of you want to get to it first and save me the time, be sure to let me know :)  :
[http://www.ubuntuforums.org/showthread.php?t=188761&highlight=layout](http://www.ubuntuforums.org/showthread.php?t=188761&highlight=layout)

---

### Post by madsen on 2007-07-14
Maybe [http://lingoland.kopula.dk/index.php/2007/07/14/ipa-input-in-linux-ubuntu-feisty-fawn/](http://lingoland.kopula.dk/index.php/2007/07/14/ipa-input-in-linux-ubuntu-feisty-fawn/) can be of interest.
A good and free Unicode font with support for the entire IPA extension is Thryomanes (it's in the package ttf-thryomanes). SILDoulous can be installed like any other TTF-font in Ubuntu (google 'install ttf ubuntu'), but it's not Unicode, which kinda sucks.

---

### Post by tubunu on 2007-09-17
One-click solution to installing IPA font on your system (well, ok, a couple of clicks...):

In Synaptic look for this and install:
```
xfonts-intl-phonetic
```

Open openoffice.org and transcribe away! :)

All IPA symbols look great!

---

### Post by John Jason Jordan on 2008-04-12
This thread is a bit old, but if anyone is still needing information on how to use IPA on Ubuntu, there is a new website covering all aspects of using IPA on a computer - which are the best fonts and where to get them, how to fix your browser to display them, and various ways to enter them in all the different office suites.

[http://ipa4linguists.pbwiki.com]("http://ipa4linguists.pbwiki.com")

---


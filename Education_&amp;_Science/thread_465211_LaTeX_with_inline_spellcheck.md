---
title: "LaTeX with inline spellcheck?"
date: 2007-06-05
forum: Education &amp; Science
---

### Post by tkjacobsen on 2007-06-05
Does anyone know a LaTeX editor with inline spellcheck? (You know the red lines under all the words)

---

### Post by Zdravko on 2007-06-05
Hmm, maybe Kile has some sort of plugin. The actual spellcheck might be done by an external application though. I am interested to know the solution :)

---

### Post by tkjacobsen on 2007-06-05
Unfortunately it doesn't look like kile has it yet
[http://osdir.com/ml/kde.devel.kile/2007-01/msg00011.html](http://osdir.com/ml/kde.devel.kile/2007-01/msg00011.html)

I will be very happy when this feature is implemented. Kile is by far the best LaTeX editor I know.

---

### Post by sam81 on 2007-06-05
Emacs with flyspell is an option, though I don't actually use it, so I can't tell if it's good...

[http://www-sop.inria.fr/mimosa/Manuel.Serrano/flyspell/flyspell.html](http://www-sop.inria.fr/mimosa/Manuel.Serrano/flyspell/flyspell.html)

---

### Post by parktownprawn on 2007-06-06
I use emacs with flyspell and its very good - i heartily recommend it.

---

### Post by tkjacobsen on 2007-06-06
I'll try it out
Thanks guys.

---

### Post by ssam on 2007-06-08
gedit has a spell check plug in

---

### Post by lucacerone on 2009-02-01
Hi everybody,
I don't know if you already could solve it,
but I found this solution about enabling Kile
to spellcheck inline!

[http://www.ubuntued.com/?p=38](http://www.ubuntued.com/?p=38)


>    1. First, you need to install the KDE control center
      sudo apt-get install kcontrol
   2. Then, open KDE control center by running the kcontrol command, navigate to KDE Components -> Spell Checker and set the spell checking Client to ASpell
   3. Spell checking will now be enabled next time you start Kile!


Maybe could be useful for some of you, as I think Kile is very good to write LaTeX documents!

Cheers, -Luca

---

### Post by m4cph1sto on 2009-02-11
> **lucacerone said:**
> Hi everybody,
I don't know if you already could solve it,
but I found this solution about enabling Kile
to spellcheck inline!


Have you gotten this to work with Intrepid? It seems there are problems, see this thread:

[http://ubuntuforums.org/showthread.php?t=964796&page=4](http://ubuntuforums.org/showthread.php?t=964796&page=4)

---

### Post by Benzjaminz on 2009-02-17
This is exactly the question I have and can't find a solution anywhere. 

Kile (latex editor) now has inline spelling but on Ubuntu intrepid this can't be activated because kcontrol no longer exists in KDE4 on ubuntu intrepid.

There must be a way to activate inline spelling on kile in ubuntu intrepid. Does anyone out there know a way?

---

### Post by InfernalNeutrino on 2009-02-17
I use (g)vim + latex-suite and it has such a feature. It's pretty nifty if you like vim.

---

### Post by skintythe1andonly on 2009-02-20
gedit has a built in spell checker and has a latex plugin you can download (cant remember where... think off the debian site) so that you have all the functionality of kile without have to go near kde

---

### Post by Benzjaminz on 2009-06-23
For people like me still waiting for kile to implement inline spelling properly, I've just found that Texmaker ([http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)) has now got inline spelling working nicely.

I've only used it once but seems to work nicely and has all the other clickable functions like Kile.

EDIT: But you have to use 1.9.1 or later. The version currently in the repositories 1.8 doesn't have inline spelling.

---

### Post by m4cph1sto on 2009-06-23
> **Benzjaminz said:**
> For people like me still waiting for kile to implement inline spelling properly, I've just found that Texmaker ([http://www.xm1math.net/texmaker/](http://www.xm1math.net/texmaker/)) has now got inline spelling working nicely.


That's great, I can do with Texmaker.  New problem now: Texmaker has no means of adding a word to the dictionary.  I do scientific writing so nearly every word I type is not in the standard dictionary.  Texmaker uses the Open Office 2 dictionary, which on my system is located at /usr/share/myspell/dicts/en_US.dic.  Is there any good way to add new words to the dictionary, apart from manually editing the text file?

---

### Post by InfernalNeutrino on 2009-06-24
I know the vim + latex-suite can do that sort of spell check (see attached for image). I like it alot (started my tex life with kile, which is also pretty slick IMO).

EDIT: I don't know about texmaker, but vim has methods to add/remove works from dictionary.... I also just realized this was a resurrected post and that I already posted before... oops!

---

### Post by Benzjaminz on 2009-06-24
@m4cph1sto

I didn't realise that. That's a real pity. Hopefully it will be added soon. Let me know if you find a good work around.

@InfernalNeutrino

I've got no problem with vim (or emacs) for programming. But for some reason I only feel comfortable with a nice GUI like Kile or Texmaker for word processing. Maybe I must get over it.

---

### Post by drd20_work on 2009-12-16
Hi Guys,

Needed this feature as well, so I've implemented it within the 1.9.2 version of Texmaker; see [here]("https://secure.nixbioinf.org/wordpress/?p=94") for the source code and usage instructions.

Good luck.

---


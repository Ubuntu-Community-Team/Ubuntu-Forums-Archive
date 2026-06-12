---
title: "GNOME or GTK text auto-completion in file name boxes"
date: 2008-02-19
forum: Desktop Environments
---

### Post by FSHero on 2008-02-19
I've had this very annoying niggle with GNOME (or GTK: I don't know what exactly I'm referring to) for a while now, and it has to be the single most important reason I prefer KDE over GNOME!

Anyway, enough babbling. I'm using Kubuntu Feisty (7.04), running Thunderbird in KDE. If I click "attach", it brings up a file name box, with the keyboard 'focus' on the text box shown in picture 1 (see the attached images below).

If I start typing e.g "/home/fs", it will autocomplete with "/home/fshero", but with the end-part highlighted, as shown in picture 2. Hence, I would still be able to type "hero" (as if to complete the name "fshero") myself.

However, I noticed that sometimes (and I can't quite figure out when systematically) when I type, it fills in the box completely automatically. So, the text 'jumps forward'. E.g. While typing "/h", it fills it with "/home", and then when I type "/f" it fills with "/home/fshero".

The only occasion where I have noticed this occurring systematically is if I press Ctrl+Tab to tab through all the options, then return back to the text-box again. Also systematic is when I select the whole text of the text box and press Backspace. After this, typing is back to 'old behaviour' (that is, the first situation I described above).

Apart from these observations, there have been times where the text box switched to the 'new' behaviour and I haven't been able to identify exactly what else does this.

The reason why this is so annoying is because I touch-type. So, when I'm typing at speed, I make mistakes with the 'new' behaviour (as I am expecting the 'old'). Thankfully I've never encountered this with any KDE dialogue boxes.

How do I turn the 'new' behaviour off with a keyboard shortcut or a permananet option? I hate having to select the text with the mouse and typing it all again!

---

### Post by AmyRose on 2008-04-18
I have to agree. This is very annoying to me too. I've been Googling around for days trying to find answers, and all I can find is people praising this annoying feature.

---

### Post by akudewan on 2008-05-05
Has anyone found a solution to this? I'm using Hardy, and now the Run dialog in Gnome is doing the same thing...

---

### Post by FSHero on 2008-05-07
@AmyRose, @akudewan:
I'm glad I'm not going crazy! So there is something fishy...!
Unfortunately I have exams to revise for at present, but after that (in 1.5 weeks time) I shall look.

AmyRose: could you give me some links about people praising this feature? I am just wondering if it has a name or something.

Maybe I'll ask in IRC. Perhaps someone should file this as a bug!

P.S. IIRC this also happens in Kubuntu 7.10 (Gutsy) amd64. It happened in Thunderbird. It is a shame to see this problem has not been removed in Hardy, as evidenced by akudewan.

---

### Post by akudewan on 2008-06-02
YES!! FINALLY I HAVE SOMETHING!!! :):):):):):):):)

This is a bug with Glipper. [https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/227406](https://bugs.launchpad.net/ubuntu/+source/glipper/+bug/227406)

I removed glipper from the panel, and the annoyance has stopped.

And I'm using Parcellite for the time being, (or maybe permanently):
[http://www.gnomefiles.org/app.php/Parcellite](http://www.gnomefiles.org/app.php/Parcellite)
[http://getdeb.net/search.php?keywords=Parcellite](http://getdeb.net/search.php?keywords=Parcellite)

---

### Post by FSHero on 2008-06-03
@akudewan: I'm glad to hear that you found out how to fix the problem! I need to find out how to do it on my Kubuntu Hardy box now! I shall report back with news.

---


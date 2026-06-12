---
title: "Evolution email spellchecker problem"
date: 2009-02-28
forum: General Help
---

### Post by Shawn K on 2009-02-28
Hello All,

I'm not sure if this is a good place to ask this or not.  So far, I've not found a forum dedicated to Evolution, so I figured that since it's bundled with Ubuntu (Intrepid at least), I'd ask here.

Recently, Evolution's spellchecker started underlining EVERY word I type, whether it's incorrect or not.  I don't see it on any emails that I read, only on ones that I compose (but even then, if I'm replying to something, it underlines all of the words in the original email, too).

If it's just a simple configuration setting issue, I've not been able to find out where it is.

If it helps at all, I'm running Ubuntu 8.10 on an Acer Aspire 5610 w/ 1GB RAM.  It was a clean-sheet install - the previous OS was completely wiped.  Evolution was working fine for about the first month that I used it, and now it's getting wonky.

Any suggestions would be greatly appreciated, and I thank you in advance.

(If this is the wrong area to ask this question, then I apologize.)

---

### Post by Kevbert on 2009-02-28
Welcome to Ubuntu.
When you compose a new message, go to Edit-Current Languages and check that the correct box is selected (it's possible to have multiple languages such as English (American) and English (British) selected) . Also check Edit-Character Encoding is set to UTF-8.

---

### Post by Shawn K on 2009-02-28
Well, that fixed part of my problem.  When I went to Current Languages, it had Turkish checked.  I unchecked it, and now it quit telling me that I'm misspelling everything (which is good, because I know nothing about Turkish).

The next problem is, Turkish was the ONLY language available.  There was NOTHING else.  So now, I have no spellchecker function at all.

My first thought is to check Synaptic to see if there are language files that I can add?

NOTE:  I just checked View -->Character Encoding in the main Evolution screen, and it had Default checked.  I switched it to Unicode UTF-8.  I noticed, though, that there were no American English options, only Western European and Western European, New.  Shouldn't there be an English (American) in the list?

---

### Post by dcstar on 2009-02-28
> **Shawn K said:**
> Well, that fixed part of my problem.  When I went to Current Languages, it had Turkish checked.  I unchecked it, and now it quit telling me that I'm misspelling everything (which is good, because I know nothing about Turkish).

The next problem is, Turkish was the ONLY language available.  There was NOTHING else.  So now, I have no spellchecker function at all.

My first thought is to check Synaptic to see if there are language files that I can add?
........

AFAIK Evolution uses gnome-spell which uses the aspell packages you have installed.

---

### Post by Shawn K on 2009-03-01
David,

You gave me the critical clue.  I opened Synaptic to check if I had any of the aspell packets installed - I didn't.  Once I added them, everything worked perfectly.  Now I have English (American), as well as a couple European variants.  Spellchecker is working great now.

Thanks for the help, guys.  I guess I made the mistake of assuming that the correct files were already in place, when I should have checked first and known for sure.

**PROBLEM SOLVED**

---


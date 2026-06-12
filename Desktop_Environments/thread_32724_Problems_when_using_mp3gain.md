---
title: "Problems when using mp3gain"
date: 2005-05-09
forum: Desktop Environments
---

### Post by feeny on 2005-05-09
prologue:
One program that linux is lacking is mp3gain (GUI). I've tried to use is through wine (win-version) but there seems to be several problems so it's not working. I know there is a command line version for linux but I don't know how it works. 

So the question is: how can I use 90db max gain in mp3gain? In windows I just needed to write "90" into a field in main screen, but I how to do it from command line?

---

### Post by feeny on 2005-05-12
^up. Anyone?

---

### Post by feeny on 2005-06-09
Anybody?

---

### Post by ioliver on 2005-06-09
I just wish I could figure out a command line to run mp3gain in album mode on all the mp3s in each directory of the machine. (mp3gain muct be invoked once per directory and given a list of all mp3s in that directory)

Might be time for some Python.

Ian

---

### Post by ioliver on 2005-06-09
Hmmm, well I worked out my issue.

find . -type d -exec sh -c "cd \"{}\" && mp3gain -a -k *.mp3" \;
seems to do it.

Ian

---

### Post by ioliver on 2005-06-11
I am now using "-a -p -k" to do album mode, preserve attributes, and don't clip.

Others use "-a -p -c", which tells it to ignore clipping.

I really am not sure what's best, and there is much debate on the issue in various forums.

Ian

---

### Post by ioliver on 2005-06-11
Feeny, I think I have found chapter and verse on this one. 

See this thread - [http://forums.afterdawn.com/thread_view.cfm/80333](http://forums.afterdawn.com/thread_view.cfm/80333)

Regards

Ian

---

### Post by palsyboy on 2005-06-13
While I don't have any tips for running it via command line, I personally use [JavaMP3Gain](http://step.polymtl.ca/~guardia/javamp3gain.php) as a graphical front-end to normalize my music collection.

---

### Post by mithras86 on 2006-07-11
> **palsyboy said:**
> While I don't have any tips for running it via command line, I personally use [JavaMP3Gain](http://step.polymtl.ca/~guardia/javamp3gain.php) as a graphical front-end to normalize my music collection.
I know the last post is from June 2005, but I'd like to know if there is a way to use mp3gain with the java gui. Or is there already a gtk2 frontend for mp3gain? I don't get javamp3gain working, so how do i get a frontend for mp3gain?
I tried "java /path_to_JavaMP3Gain.jar /usr/bin/mp3gain" but that didn't seem to work. Anyone an idea?

---

### Post by koshari on 2006-07-19
"I'd like to know if there is a way to use mp3gain with the java gui"

yes i use it, i use track gain to normalise all my music to 89 dB to do this in mp3gain java gui i need to tick the "suggested gain"box and add the db gain in a decimal, 89 = .89

"is there already a gtk2 frontend for mp3gain?"

not that i have found, wish i had some experiance in this field so i could have a crack, might be a good "hello world" project for me.


I tried 
"java /path_to_JavaMP3Gain.jar /usr/bin/mp3gain" but that didn't seem to work. Anyone an idea?

try this
<path to java.exe> -jar <path to JavaMP3Gain.jar>

and heres the link to the file if you havnt downloaded it already, 
[http://step.polymtl.ca/~guardia/javamp3gain.php](http://step.polymtl.ca/~guardia/javamp3gain.php)

---

### Post by palsyboy on 2006-07-20
I'm sorry that I didn't get back to you sooner, mithras86.  My computer was down at that time, and then I forgot.  I'm glad that koshari was able to answer your question.

---

### Post by palsyboy on 2006-07-20
And just in case you run into trouble, check out this thread: [http://www.ubuntuforums.org/showthread.php?t=95650](http://www.ubuntuforums.org/showthread.php?t=95650)

---


---
title: "Xserver wont't start (might have to do with me having removed evolution..)"
date: 2010-06-27
forum: Desktop Environments
---

### Post by isync on 2010-06-27
Today my xserver suddenly won't start beyond the login, after I entered my credentials the screen goes black and I can see and move around the mouse but after a last read sound from my hdd it won't go any further, about 1 sec after <entered credentials>+ENTER.

I did the recommended apt-get updates today. But I don't think this broke my GUI. But what I did was "hey why don't free a few MB and remove this unwanted unneeded evolution and epiphany from the system".

After the next boot hangs I now know what "default application" means. Is it true I can't remove evolution without breaking my GNOME? Is this the cause?

On command line I reinstalled both, apt-get install epiphany evolution, but what about all those other libs I deinstalled, all those beginning with evolution-* like evolution-common evolution-couchdb evolution-exchange evolution-indicator evolution-plugins evolution-webcal...

Any ideas for a fix? Any magic command who scans fi x-server has everything he needs to boot?

I poked around the various logfiles but strangely my error does not seem to trigger any common log/error to pop up (/var/log/dmesg,syslog,bootlog). (Where should I look?)

---

### Post by punsingh on 2010-06-28
I think I am facing the same problem. How did you fix it (if eventually you did) ?

---

### Post by isync on 2010-06-28
The same?? This means it might be unreleated to my evolution removal... 

Did you do the regular updates, just as me?

(No solution yet, as I was too frustrated  to boot that machine till then)

---

### Post by punsingh on 2010-06-28
Hi
I was trying to load gtk+. I did make, make install. Then I ran ldconfig. Next time I booted, I had a black screen with a mouse pointer. I was able to get to the command line from recovery mode and also by ctrl-alt-f1. No GUI is working. I did the updates but no luck. I reinstalled GNOME and KDE desktop. Nothing seems to be working. 
If I do startx, I get an error message,Server is already active for display 0.
In recovery mode, failsafe graphics is also not functioning. I come back to the command line.
 
I think the problem has got to do with some linking with the libraries. Thats what ldconfig does right? 
 
Hope for a simple solution.

---

### Post by XSAlliN on 2010-06-28
I don't understand you guys. Missing basic knowledge yet you toy with CLI as if anything goes (most does, but you have to know how to fix it if things go wrong).

When removing something from Ubuntu: USE SYNAPTIC - but don't just remove them in the windows way (click -> remove and then hit Yes ignoring the rest...). Cause in synaptic you can also see the dependencies you remove.

Removing evolution-data-server (for example) you also loose:

[IMG]http://img413.imageshack.us/img413/1248/screenddddshot.png[/IMG]

- which you obviously need it for gnome.

---

### Post by isync on 2010-06-28
@XSAlliN: you're so right... I remember this exact list you posted flying by but was too fast on the "click" and thought "ubuntu's Gnome won't be so interwoven with evolution that it hurts"... Now I know better... Thanks for the list of what I removed!

BTW: "toy with CLI", "the windows way"!? After 5+ years of ubuntu + debian wrangling this was a deadly stab! Arg.

Hope re-installing this list of packages will bring x back - fingers crossed.


@punsingh: sounds like a different route... If you accidently removed gnome-* like me this thread might already have helped you. If not, someone more knowledgeable than me needs to assist you. sorry.

---

### Post by XSAlliN on 2010-06-29
> "toy with CLI", "the windows way"!? After 5+ years of ubuntu + debian wrangling this was a deadly stab! Arg.

Time is irrelevant, some have more than 10 years with many distribution and still threat some things "the Windows way".

And by Windows way (as mentioned above), I'm referring to the part where people don't pay attention to what they're doing... just "next -> Next (clicking without looking)". And same goes for CLI where many use "Copy + Paste" but don't try to understand what they're doing... and sometimes times, things go wrong and they end up confused, not realizing what have they done  wrong(which is pretty obvious since they didn't paid attention to that part).

---

### Post by isync on 2010-06-30
sudo apt-get install gnome-core

brought x back.

---


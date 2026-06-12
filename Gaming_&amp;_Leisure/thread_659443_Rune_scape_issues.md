---
title: "Rune scape issues"
date: 2008-01-05
forum: Gaming &amp; Leisure
---

### Post by Yourfalseking on 2008-01-05
I used i.e Firefox and epiphany

i have the most updated version of Java

And when i open up runescape

i get a Blank box where the game should be..
 
[COLOR="Red"]Why???!!!?![/COLOR]

---

### Post by Yourfalseking on 2008-01-05
bump

---

### Post by snowstorm167 on 2008-01-05
I have a little problem with runescape myself. when I log in I must walk around for 5 mins before I can play.Is there some way I can fix this or would jagex be the spot for support on this.

---

### Post by AdNZL on 2008-01-05
I have exactly the same issue, but it is will all web based java apps.

As far as I can tell it is because firefox on ubuntu will only use the old version of java even if you have the new version installed. Nobody seems to be able to fix this problem. For some people it works and for others it doesn't. You could try reinstalling Java, but if this doesn't work I'm affraid your probably out of luck.

If you go to [www.java.com](www.java.com) there is a test there to check what version of Java your browser is using. when I do it it comes back with version number 1.42 or something like that, which is well out of date.

I've also noticed there only seems to be a toggle switch for java in fire fox, to either switch it on or off, but no options as to what version to use. Oh yeah, and just incase make sure you have Java enabled in firefox, but I think its on by default anyway.

---

### Post by mig5 on 2008-01-09
OK, firstly to work out which version of java firefox is using you should try typing this into the firefox address bar:
```
about:plugins
```

On the page that comes up you should see a list of various plugins, one of which will be java.  For runescape to work nicely you should have Sun Java 1.6 listed.  By default, when you first try to run something that needs java ubuntu offers to install a free version of java which isn't Sun java, so that is probably what you have installed.

To get Sun Java 1.6 you need to enable the universe/multiverse repositories (its one or the other, I have both enabled) and search for sun java in synaptic and install the one that has sun java 6 plugin in the name.

---

### Post by RSrealo on 2008-01-18
I play Runescape on my 5yrs old hp using Ubuntu Feisty and its a miracle running wtih 50s average cpu% usage:)

Anyways, I have tried Sun Java6 and Java5, Java5 seems to be more stable for me on my browsers running runescape


Sudo apt-get install Sun-Java5-jre 
Sudo apt-get install sun-java5-plugin

it works for me, i hope it will for you.

---

### Post by some_random_noob on 2008-01-18
I played RS a few months ago on my Gutsy computer (I got java from the repos). I also have a friend who was running it in Ubuntu. I don't know exactly how to help, but fiddle around a bit and it should work.

Be sure to check that Java is enabled in Firefox's preferences too.

---

### Post by amaisim on 2008-01-18
I had the same problem when in the middle of the game, the screen turned gray.   While one can still play on, but the game lost all colour.   Just fixed it with downloading Sun Java Version 6.   It seem stable for the last 4 hours of continuous RunScape (ya, i know, thats a long time).  Do this:
System-Administration-synaptic Package Manager  Then type Sun Java on the Search box, a whole list of available Sun Java get listed, scroll down to almost the end, click on Sun Java 6 and the one below it.   Then click apply.
Hope this help, and do not give up Linux and go back to the You Know What.

Regards,
Amaisim

---


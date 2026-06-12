---
title: "&quot;Unable to get exclusive lock&quot; when trying to Add application"
date: 2006-03-17
forum: Desktop Environments
---

### Post by Jeff_forssell on 2006-03-17
After trying unsuccessfully to install Java, if I try to "add application" I get:

"Unable to get exclusive lock

Det här betyder oftast att en annan pakethanterare (som apt-get eller aptitude) redan körs. Vänligen stäng det programmet först"

where the swedish means about: "This usually means that another package handler (like apt-get or aptitude) is already running" 

But I haven't started anything else. (And I have restarted my system)

Any suggestions?

---

### Post by towsonu2003 on 2006-03-17
it's possible that apt-get is running in the backround to search updates. see with ps aux | grep apt 
also, if open, close synaptic.

---

### Post by Jeff_forssell on 2006-03-19
Thanx for suggestion.
tried that now, got 
"jeff@ubuntu-Aopen:~$ ps aux | grep apt
jeff     11935  0.0  0.1   3680   740 pts/0    R+   18:16   0:00 grep apt"

Which doesn't make me much more enlightened
and I still get the same error if i try to start "add applications"
:-?

---

### Post by seedman on 2006-03-19
I got the same thing on mine, and don't know what to do.  
I've already had to re-install twice from my short-sighted playfull ignorance so I get really nervous using the command line without some background. (where do we get lots of background??
I'll reply again if I find anything.

---

### Post by seedman on 2006-03-19
I found my answer at:penguinchrissy 1-07-2006 "Can not update"

There are many options there  and I tried several. One of them worked! I wish I had paid more attention to which one it was...
 
Good luck!

---

### Post by towsonu2003 on 2006-03-19
[QUOTE=Jeff_forssell]Thanx for suggestion.
tried that now, got 
"jeff@ubuntu-Aopen:~$ ps aux | grep apt
jeff     11935  0.0  0.1   3680   740 pts/0    R+   18:16   0:00 grep apt"

Which doesn't make me much more enlightened
and I still get the same error if i try to start "add applications"
:-?[/QUOTE]
your error says that apt-get is being used by something else (unablilty to get exclusive lock). comon programs that use this include synaptic and that "add programs" tool. but your output says that apt is not running on your machine (when you typed the command).  so, to me, something wasn't automatically refreshed (it plays around with a lock file) properly when apt-get exited last time. 

Try to google the error message in quotes + apt-get on google.com/linux while waiting for someone who knows this to see your post.

---

### Post by Jeff_forssell on 2006-03-20
There was en error message when I (tried to) install Java SUn. It said I had to manually do something. I copied what it said and tried to paste it in the terminal but I honestly don't remember if nothing happened (or if I was still fighting with getting my su status).  I remeber that the message didn't feel like it was quite complete. It felt like I would probably just open a pandoras box with options I wouldn't understand. But that may just be paranoia.:-k 

I assume that the java installation process is complicated bu some SUN control issue. (or is that more paranoia?)  Otherwise I would think it would be default installed.

Anyhow it might be that unknown step in the Java install process that is still locked.

---

### Post by towsonu2003 on 2006-03-20
[QUOTE=Jeff_forssell]
Anyhow it might be that unknown step in the Java install process that is still locked.[/QUOTE]
You could try to find that command: type history and hit enter. this will give you the last 500 commands you issued. Hopefully, it is still there? If it is, post it here. Although I'm pretty sure I won't be able to understand it, someone will sooner or later. 

Did you manage to find the post seedman refers to? 
[quote=seedman]I found my answer atenguinchrissy 1-07-2006 "Can not update"[/quote]

---

### Post by Jeff_forssell on 2006-04-23
I tried the history command but it didn't turn up anything useful.

I tried putting in:

sudo apt-get install sun-j2re1.5 java -version
again, and this came:

apt 0.6.40.1ubuntu9 för linux i386 kompilerad den Oct  5 2005 13:40:08
Moduler som stöds:
 Ver: Standard .deb
 Pkg:  Debian dpkg interface (Priority 30)
 S.L: 'deb' Standard Debian binary tree
 S.L: 'deb-src' Standard Debian source tree
 Idx: Debian Source Index
 Idx: Debian Package Index
 Idx: Debian dpkg status file
E: Kommandoradsflagga "e" [från -version] är ej känd.

I don't know what that means or if if did anything.

---


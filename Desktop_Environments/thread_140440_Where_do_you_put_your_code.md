---
title: "Where do you put your code?"
date: 2006-03-06
forum: Desktop Environments
---

### Post by DJiNN on 2006-03-06
There is much information in this forum, and much of it in the form of snippets of code to be pasted etc, into a terminal window.  It's a great way to learn how to use the terminal & hopefully improve your knowledge of Linux/Ubuntu etc.

But, i have noticed that, often (for me anyway) i have to use the same piece of code again at some later date, and by then i have completely forgotten what thread it was written in etc.

So, i have decided to "Save" the clips of info in one place so that i can refer to them at a later date if needed, and also to share with others if i can. 

What i would like to ask, is A:) if there are others doing this? & B:) what piece of software (if any) do you use to store such pieces of info? 

I was thinking of using TomBoy because it's small & fast, but obviously it's not built to do this, although i'm sure that it's capable. I'm sure there are other (better?) programs which are capable of doing this but as of yet i don't know what they are.

Thanks for taking the time.......

DJiNN

---

### Post by knalle on 2006-03-06
i use my **Pivot** driven blog for notebook, i just file it under linux and add it to my blog.

---

### Post by steevc on 2006-03-06
I tend to save things as draft emails. I'm using IMAP, so I can access them from anywhere.

---

### Post by DJiNN on 2006-03-06
[QUOTE=knalle]i use my **Pivot** driven blog for notebook, i just file it under linux and add it to my blog.[/QUOTE]

**Pivot**....? What's that? Is it a prog for Linux that allows you to write your blogs offline etc? I'm only just getting into blogging & have just signed up with Live Journal..... haven't done anything yet though i'm looking forward to doing so, and also finding out more about it! :)

Thanks for answering......

DJiNN

---

### Post by knalle on 2006-03-06
[http://www.pivotlog.net/](http://www.pivotlog.net/) is a great php driven blog generator that doesn't need a database, everything is stored in flat files, and upon new enteries static xhtml is generated,

try it, i have tried some different blog systems and pivot is the best so far, imo.

visit my blog at : [http://lamers.tv/](http://lamers.tv/) to see an example of how i use pivot.

---

### Post by leech on 2006-03-06
I have a MUCH better solution for repeating commands that you can't remember the full thing.  If you can remember any of it at all, use Control+R.  What this will do inside a terminal is look in your .bash_history file and match whatever is in there with what you start typing.  For example, if previously you had to EXPORT gcc GCC-VERSION=3.4 or something like that, you can just hit Control+R in a terminal and start typing "EX" and it will auto-complete it for you.

Leech

---

### Post by knalle on 2006-03-06
yeah, but bash history is not endless, and is volatile. and you cannot annotate your commands

---

### Post by IYY on 2006-03-06
I just have a text file called notes.txt in my home directory. I edit it with **vim**, and read it with **less**. If it's just a small addition of a couple of lines, I use **cat >> notes.txt**.

---

### Post by DJiNN on 2006-03-06
[quote=knalle][http://www.pivotlog.net/]("http://www.pivotlog.net/") is a great php driven blog generator that doesn't need a database, everything is stored in flat files, and upon new enteries static xhtml is generated,

try it, i have tried some different blog systems and pivot is the best so far, imo.

visit my blog at : [http://lamers.tv/]("http://lamers.tv/") to see an example of how i use pivot.[/quote]

Thanks for the info. I've downloaded Pivot & been having a look, but i think i need to understand more about blogging per se first of all, before i delve into Pivot etc.  Great blog site you have though...... where do you host it? Is it just the standard server space that you get from your isp?

DJiNN

---

### Post by knalle on 2006-03-06
[QUOTE=DJiNN]where do you host it? Is it just the standard server space that you get from your isp?
DJiNN[/QUOTE]


thanks, i host at a isp in texas huston, running redhat and LAMP

---

### Post by engla on 2006-03-06
[QUOTE=knalle]yeah, but bash history is not endless, and is volatile. and you cannot annotate your commands[/QUOTE]
There are some ways to make the history much more powerful, see
[Power shell usage: Bash Tips & Tricks]("http://www.ukuug.org/events/linux2003/papers/bash_tips/")

Nice Tweaks:
comm + right arrow completes to previous 'command' and other things that start with 'comm' (example)
History from multiple sessions is appended, not replaced and more

---

### Post by knalle on 2006-03-06
[QUOTE=engla]There are some ways to make the history much more powerful, see
[Power shell usage: Bash Tips & Tricks]("http://www.ukuug.org/events/linux2003/papers/bash_tips/")
[/QUOTE]

great stuff, thanks! :)

---

### Post by DJiNN on 2006-03-06
[quote=leech]I have a MUCH better solution for repeating commands that you can't remember the full thing.  If you can remember any of it at all, use Control+R.  What this will do inside a terminal is look in your .bash_history file and match whatever is in there with what you start typing.  For example, if previously you had to EXPORT gcc GCC-VERSION=3.4 or something like that, you can just hit Control+R in a terminal and start typing "EX" and it will auto-complete it for you.

Leech[/quote]

That's interesting, i completely forgot about using the built in history. :) Not quite what i meant though.... more like a "Permanent" place to store the many snippets of code & stuff that you get from the various threads etc, so that, say, in a month or two, if you want to do something that you did previously (a few months ago) but can't remember what the command was/is, you can just go to where all the different "snippets" are stored & just copy & paste. :)

Eventually i guess that you would start to remember different things that you use, but in the beginning it could certainly help to store them all in one place.

Thanks for the reply.....

DJiNN

---

### Post by DJiNN on 2006-03-06
[quote=knalle]thanks, i host at a isp in texas huston, running redhat and LAMP[/quote]

Do you have to pay for the service or is it free? The basic kind of "Live Journal" or "Blogger" site seems OK (Which is what i think i'll start with) but i can't see them allowing me to upload something like Pivot.... i would need something more for that i guess? 

It's all a learning curve eh? :)

Thanks for the help......

DJiNN

---

### Post by DJiNN on 2006-03-06
[quote=IYY]I just have a text file called notes.txt in my home directory. I edit it with **vim**, and read it with **less**. If it's just a small addition of a couple of lines, I use **cat >> notes.txt**.[/quote]

That's kind of what i was going to do, but using something like TomBoy or Sticky Notes.  Nice one....... :)

DJiNN

---

### Post by knalle on 2006-03-06
[QUOTE=DJiNN]Do you have to pay for the service or is it free?
[/QUOTE]

i pay about $15 a mount for 10gb, and they allow me to upload any php i want.

if your a bit of a hacker get the cheapest LAMP ISP you can find and maintain the PHP yourself, hosted blogs suffer from restrictions and heavy load

---

### Post by DJiNN on 2006-03-06
[quote=knalle]i pay about $15 a mount for 10gb, and they allow me to upload any php i want.

if your a bit of a hacker get the cheapest LAMP ISP you can find and maintain the PHP yourself, hosted blogs suffer from restrictions and heavy load[/quote]

Good price, but i'm not at all a hacker & i haven't a clue what LAMP is. :)  I think i have got a lot to learn yet before i start down that road.... seems like a lot of hassle. I thought it was a bit more straightforward than that. :)

DJiNN

---

### Post by Zwack on 2006-03-06
I use gJots2 for a lot of scribbled notes...  Each note gets put into it's own page...
Some notes are grouped together by categories... 

oh and I make the top line relevant so that I can see it in the tree view.  the gjots file is portable, but I don't view it outside home.  Most of the time I use it to sort out my thoughts on a given subject and then I can usually transfer the completed outline into a more specific plan of action.

Z.

---

### Post by DJiNN on 2006-03-07
[quote=Zwack]I use gJots2 for a lot of scribbled notes...  Each note gets put into it's own page...
Some notes are grouped together by categories... 

oh and I make the top line relevant so that I can see it in the tree view.  the gjots file is portable, but I don't view it outside home.  Most of the time I use it to sort out my thoughts on a given subject and then I can usually transfer the completed outline into a more specific plan of action.[/quote]

Thanks for the reply..... that sounds quite a useful little program. Is it a desklet type of thing or something else? I've looked on my system but can't find it anywhere, but would love to give it a try.

DJiNN

---

### Post by MichaelZ on 2006-03-07
[QUOTE=engla]There are some ways to make the history much more powerful, see
[Power shell usage: Bash Tips & Tricks]("http://www.ukuug.org/events/linux2003/papers/bash_tips/")
[/QUOTE]

Interesting and useful :). Thanks.

Best wishes,
Michael

---


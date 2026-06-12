---
title: "Alternative to conky anyone??"
date: 2009-12-19
forum: Desktop Environments
---

### Post by bix15 on 2009-12-19
I'm lookin' for a alternative to a program called conky. If anybody knows what im talking about then you might just have an answer for me.
Conky is a system monitoring tool.....here i'll just give you a picture.

[http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg](http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg)

I've given up on conky....it's a major pain and not worth my time.
sooooo, if any of you guys knows an alternative, just by pure chance (it doesn't exactly have to be the same, you get the gist of it.....) I would VERY much like to know!!

---

### Post by louieb on 2009-12-20
gkrellm

---

### Post by londonali1010 on 2009-12-20
> **bix15 said:**
> I'm lookin' for a alternative to a program called conky. If anybody knows what im talking about then you might just have an answer for me.
Conky is a system monitoring tool.....here i'll just give you a picture.

[http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg](http://gnome-look.org/CONTENT/content-pre1/74813-1.jpg)

I've given up on conky....it's a major pain and not worth my time.
sooooo, if any of you guys knows an alternative, just by pure chance (it doesn't exactly have to be the same, you get the gist of it.....) I would VERY much like to know!!

Sad to hear you've given up on Conky...Those of us who use it regularly really like it!  Before you switch, have you tried posting on [the Conky thread]("http://ubuntuforums.org/showthread.php?t=281865") to get some help?

---

### Post by MooPi on 2009-12-20
I'm with "londonali1010" on this one. Conky is a great tool and it uses such few resources, whats not to like. I've used it but currently don't have it on my desktop.

---

### Post by bix15 on 2009-12-20
Alright. Well here's my problem....
I used apt-get to install it. Then I simply put the .conkyrc file into my home folder.
(I configured it by copy/paste a text file I found on a website....this might be my problem. If you guys could tell me how to configure it correctly that would solve all of my problems.) 
After putting the .conkyrc file into my home folder, I opened a terminal and typed
"conky -a top_right". After that the terminal just gave me a few lines of errors such as....

Conky: /home/spencer/.conkyrc: 30: no such configuration: 'on_bottom'
Conky: border_margin is deprecated, please use window.border_inner_margin instead
Conky: use_spacer should have an argument of left, right, or none.  'no' seems to be some form of 'false', so defaulting to none.
Conky: /home/spencer/.conkyrc: 94: no such configuration: 'xmms_player'
Conky: got an endif without matching if
Conky: X Error: type 0 Display 24741c0 XID 0 serial 30 error_code 3 request_code 61 minor_code 0 other Display: 24741c0

Aborted


Do you guys spot anything wrong? 
I would very much like to get it working so help configuring it would be a huge help since that seems to be my issue.

Thanks a million!

---

### Post by zlatkart on 2009-12-20
you should post your conkyrc . You should not have to start conky this way. What is your problem with conky?

---

### Post by bix15 on 2009-12-20
My problem is that I can't/don't know how to get it cofigured.
I downloaded conky already, I just need to get it working.
A step-by-step guide would be great but I cant find one that has worked for me anywhere.
I've googled my *** off X(

Oh and if this helps at all, I'm running Karmic

---

### Post by londonali1010 on 2009-12-20
> **bix15 said:**
> My problem is that I can't/don't know how to get it cofigured.
I downloaded conky already, I just need to get it working.
A step-by-step guide would be great but I cant find one that has worked for me anywhere.
I've googled my *** off X(

Oh and if this helps at all, I'm running Karmic

First things first, have a look at [Conky Hardcore!]("http://conky.linux-hardcore.com/") They have some great info for beginners, and even a [basic .conkyrc]("http://conky.linux-hardcore.com/?page_id=173") that's been tried and tested over the years! If you still have issues, post your .conkyrc file in the [Conky thread]("http://ubuntuforums.org/showthread.php?t=281865") (you can skip straight to the end of it; there are over 11,000 posts!) and there are loads of people who are willing to help sort you out!

From what you've said, it sounds like that .conkyrc isn't quite right...I'm guessing that you copied it in from someone else's config? It may be for an old version of Conky.

---

### Post by bix15 on 2009-12-20
Hey thanks a lot for helping me!!!
After tinkering for a couple hours, I got it to look exactly the way I wanted!! XD
And thanks for the links too! They were VERY helpful.
Take a look....

---

### Post by stinkeye on 2009-12-21
> **bix15 said:**
> Hey thanks a lot for helping me!!!
After tinkering for a couple hours, I got it to look exactly the way I wanted!! XD
And thanks for the links too! They were VERY helpful.
Take a look....
Thats actually an old config of mine which uses conkyforecast and custom templates which I don't have any more.
Also you don't have all the fonts. eg ${font LCDMono:size=55}.
Also it appears you don't have hddtemp installed and you haven't changed the paths to your hard drives to correspond to your own set up.
Your better off starting from scratch so you have everything you need, and start with a simple conky.
This tutorial by Bruce is very good [_[COLOR="DarkRed"]HOW TO: A Beginners Guide to Setting up Conky[/COLOR]_]("http://ubuntuforums.org/showthread.php?p=5436679#post5437628")
Need help go here [_[COLOR="#8b0000"]http://ubuntuforums.org/showthread.php?t=281865&page=1114[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=281865&page=1114")

This is what it should look like:

---

### Post by Eskobar on 2009-12-31
Excellent... Somebody should mark this solved.

---


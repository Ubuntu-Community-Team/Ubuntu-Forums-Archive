---
title: "Gnome XGL Window Effects"
date: 2006-08-08
forum: Desktop Environments
---

### Post by Sethro on 2006-08-08
Well I have been happily using ubuntu + XGl and let me be the first to say it kicks ***.

But one thing has been killing me. Whenever I try to resize a window it _very_ slow
but XGl runs like a champ.. anybody have a fix??

---

### Post by Sethro on 2006-08-08
Oh yeah and when i open terminal the entire windows is about 35% transparent. How do i make it so that the windows border stays normal???

---

### Post by deeek on 2006-08-08
> **Sethro said:**
> Well I have been happily using ubuntu + XGl and let me be the first to say it kicks ***.

But one thing has been killing me. Whenever I try to resize a window it _very_ slow
but XGl runs like a champ.. anybody have a fix??
You might want to open up gconf-editor and go to the /apps/compiz/plugins/resize/allscreens/options and make sure the option select_texture is selected.  It will definately speedup resizing windows, however, you might get strange windows behavior though (but nothing serious).

[QUOTE=Sethro]Oh yeah and when i open terminal the entire windows is about 35% transparent. How do i make it so that the windows border stays normal???[/QUOTE]

Unfortunately, at the moment, there is no plugin that allows you to make certain parts of a window transparent.   There is a terminal app with a transparent screen and normal borders.  It is called urxvt and you can find out how to install it by going [here]("http://www.compiz.net/topic-1652-howto-rxvt-unicode-with-true-transparency-dapper").

---

### Post by scotty2hott2k on 2006-08-08
Xgl is indeed Uber,

[Here is a screenshot of my desktop using it]("http://img120.imageshack.us/img120/584/screenshotqr0.png")

---

### Post by deeek on 2006-08-08
> **scotty2hott2k said:**
> Xgl is indeed Uber,

[Here is a screenshot of my desktop using it]("http://img120.imageshack.us/img120/584/screenshotqr0.png")
Cool vist-like.

---

### Post by Sethro on 2006-08-08
Afraid it did not help, whenver i resize it stops and resizes.. dang it! lol

Oh well gotta live with it i guess??

Like I was saying about the terminal just have the black part tranparent and not the window border...

---

### Post by Sethro on 2006-08-08
Guys let me tell you one thing about Windows Vista ..... it sucks privates... lol

Its slower than my granie.. no seriously.

I have a Pentium 4 3.06Ghz Hyper Threading Processor and I was sitting doing nothing I got about 30% CPU Usage..

Vista could not recongnise any of my hardware, it was sad..

Windows Vista = Windows ME

ubuntu recongised everthing on my computer no driver no hassle.. i was so impressed..

---

### Post by deeek on 2006-08-08
> **Sethro said:**
> Afraid it did not help, whenver i resize it stops and resizes.. dang it! lol

Oh well gotta live with it i guess??

Like I was saying about the terminal just have the black part tranparent and not the window border...
Really, the stretch_texture option did not help?  That is really odd.  As far as the transparent terminal, did you check out my link?  urxvt doesn't have all of the features of gnome-terminal, but it does have the transparent black part.  ;-)

---

### Post by Sethro on 2006-08-08
Yeah I got it up and working... 

U DA MAN DEEEK

---

### Post by gruffy-06 on 2006-08-08
Windows Vista is still a beta release, given that. But forget Windows forever, because there is always GNU/Linux at your pleasure.

---

### Post by deeek on 2006-08-08
> **Sethro said:**
> Yeah I got it up and working... 

U DA MAN DEEEK
No problem.  ;)

[QUOTE=gruffy-06]But forget Windows forever, because there is always GNU/Linux at your pleasure.[/QUOTE]
[QUOTE=Sethro]Guys let me tell you one thing about Windows Vista ..... it sucks privates... lol

Its slower than my granie.. no seriously.

I have a Pentium 4 3.06Ghz Hyper Threading Processor and I was sitting doing nothing I got about 30% CPU Usage..

Vista could not recongnise any of my hardware, it was sad..

Windows Vista = Windows ME

ubuntu recongised everthing on my computer no driver no hassle.. i was so impressed..[/QUOTE]

I agree.  I will only touch windows when absolutely necessary.  Ubuntu+XGL/Compiz owns all.

---

### Post by Sethro on 2006-08-08
Say guys... when do you think ubuntu will official come with XGl...

I have used Windows XP and Mac 10.4

Ubuntu + XGL is amazing, nothing like it...

My computer fan is hardy ever on, in Windows it was constantly blazing..

Iam really impressed with ubuntu, can i go far enough to say that ubuntu is the best linux distro in town... who's with me??

---

### Post by deeek on 2006-08-08
> **Sethro said:**
> Say guys... when do you think ubuntu will official come with XGl...

I have used Windows XP and Mac 10.4

Ubuntu + XGL is amazing, nothing like it...

My computer fan is hardy ever on, in Windows it was constantly blazing..

Iam really impressed with ubuntu, can i go far enough to say that ubuntu is the best linux distro in town... who's with me??
I really don't think ubuntu will ever come with XGL standard, because it requires non-GPL video drivers from ATI or nVidia.  Take a look at what happened with the Kororaa live cd with XGL.

---

### Post by aircool on 2006-10-07
being the n00biest here, how do you do/get the vista like effects you have

ive tried vista beta , but im soooo curios to try linux out

thanks for any replies

---


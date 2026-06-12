---
title: "Quick question please!"
date: 2009-05-07
forum: General Help
---

### Post by Tipped OuT on 2009-05-07
**EDIT:** Okay, let me clarify for you guys, I have compiz fusion and emerald at the moment, works great! BUT...the blur plug-in does not work. Why? Because my graphics card doesn't support it. Then what can you do you know? Well, I heard Beryl has a "fake blur" plug-in that enables blur for graphic cards that do not have blur support. Since Beryl isn't a option now..is there any way to do this with Compiz?

Thanks :)

---

### Post by KhurramM on 2009-05-07
Hi

U will have to risk this.

Install beryl

Remove unwanted window managers = compiz

See if the gconf-editor

supports in Desktop > gnome > applications > window manager

sees and starts to use it.

Hope u get a way.

---

### Post by pjones0404 on 2009-05-07
as far as i know beryl is no longer supported. It is now compiz. you would have to find a repo that has it or install it from source. The key is that it is not longer being developed so if there are any issues or bugs they will not be fixed. 

The only thing that is built into to ubuntu is compiz in the recent releases. There is no version of ubuntu with beryl built in.

---

### Post by BslBryan on 2009-05-07
Hello, Tipped OuT. :-)

Firstly, Beryl is inactive, and has been for some time.  They merged with Compiz a while ago.  That being said, since they did merge, Beryl's Emerald can still be used with Compiz, but you first need to install it.  It's in the repositories, though, so simply 
```
sudo apt-get install emerald
```

After installing Compiz's Emerald, you should have an Emerald theme manager in a menu, which will allow you to open the theme. :-)

Also, make sure to not forget that you need to switch to emerald with "emerald --replace" before it will actually show up.

I hope I've been of some help, Tipped OuT.  

Best to you, and good luck. :-)


EDIT: Woah!  Don't do what KhurramM is suggesting.  There's no need for that.  We're not even sure if that would function.  The last thing you need is Jaunty to crash completely over a blur effect.  ;-)

---

### Post by colau on 2009-05-07
Would anyone please give the command to install compiz-fusion in ubuntu 9.04?

---

### Post by Tipped OuT on 2009-05-07
> **colau said:**
> Would anyone please give the command to install compiz-fusion in ubuntu 9.04?
You can just go to add/remove programs and search for compiz. Then download CCSM.

And to everyone else, I understand it is not supported any more, but unless there is a way to have blur with Compiz without fragment support then that's my only choice.

---

### Post by BslBryan on 2009-05-07
> **Tipped OuT said:**
> You can just go to add/remove programs and search for compiz. Then download CCSM.

And to everyone else, I understand it is not supported any more, but unless there is a way to have blur with Compiz without fragment support then that's my only choice.

Tipped OuT, just read my post.

I told you how to enable Emerald and replace the normal Compiz settings, so you can get blur again.

---

### Post by Tipped OuT on 2009-05-07
Thanks, but I do have emerald installed, and yes I have the "emerald --replace" going....still no blur. Am I missing something? I'm sorry.

---

### Post by BslBryan on 2009-05-07
Hm...

In mine, in System --> Administration --> Advanced Desktop Effects Settings, it's under "Effects."

How odd. 

I'm sorry I couldn't have been of greater help, Tipped OuT.

I suppose the only advice I can give you is to not stop searching for an answer.  Good luck. :-)

---

### Post by colau on 2009-05-07
> **Tipped OuT said:**
> You can just go to add/remove programs and search for compiz. Then download CCSM.

And to everyone else, I understand it is not supported any more, but unless there is a way to have blur with Compiz without fragment support then that's my only choice.
Can't find searching compiz in add-remove.

---

### Post by Tipped OuT on 2009-05-07
Okay, let me clarify for you guys, I have compiz fusion and emerald at the moment, works great! BUT...the blur plug-in does not work. Why? Because my graphics card doesn't support it. Then what can you do you know? Well, I heard Beryl has a "fake blur" plug-in that enables blur for graphic cards that do not have blur support. Since Beryl isn't a option now..is there any way to do this with Compiz?

Understand now :confused:

---

### Post by BslBryan on 2009-05-07
All right then.  :-?

Anyway, I'm glad you ended up getting it working. :-)

---

### Post by Tipped OuT on 2009-05-07
> **BslBryan said:**
> All right then.  :-?

Anyway, I'm glad you ended up getting it working. :-)
:confused:

XD

---

### Post by colau on 2009-05-07
> **Tipped OuT said:**
> You can just go to add/remove programs and search for compiz. Then download CCSM.

And to everyone else, I understand it is not supported any more, but unless there is a way to have blur with Compiz without fragment support then that's my only choice.
Can't find searching compiz in add-remove.

---

### Post by Tipped OuT on 2009-05-07
Oh I'm sorry dude, I ignored you :P. 

[B]sudo apt-get install compizconfig-settings-manager
[/B]
There you go =] Check in    System< Preferences for Compiz Config after you are done and have fun.

---

### Post by colau on 2009-05-07
> **Tipped OuT said:**
> Oh I'm sorry dude, I ignored you :P. 

[B]sudo apt-get install compizconfig-settings-manager
[/B]
There you go =] Check in    System< Preferences for Compiz Config after you are done and have fun.
Many thanks.It works.

---

### Post by Tipped OuT on 2009-05-07
NP. Glad I could lend a helping hand. :)

---

### Post by BslBryan on 2009-05-07
> **Tipped OuT said:**
> :confused:

XD

Oops. :oops:  Misread your previous post. :-)

Anyway, sorry I didn't come back to help, considering I *did* misread it, I didn't think there was a problem anymore. #-o

---


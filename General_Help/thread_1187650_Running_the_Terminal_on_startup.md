---
title: "Running the Terminal on startup"
date: 2009-06-14
forum: General Help
---

### Post by pat13nc3 on 2009-06-14
Hello,

I have begun to find I use the terminal more than anything else,
As such I would like to just have it run upon startup,
Saving me the time to have to open it every time I log on.

I am running Ubuntu 9.04 Jaunty Jackalope
And I found something promising under System > Preferences > Startup Applications
However I was unable to figure out how to set it up using that tool.

Can somebody please help me figure this out?

---

### Post by blueridgedog on 2009-06-14
Can you specify "gnome-terminal" as an application using the menu you mentioned?

---

### Post by loomsen on 2009-06-14
Go System > Preferences > Startup Applications
Hit new
Add some fancy name & comment (whichever you like)
command: gnome-terminal

Or whichever terminal you prefer.

---

### Post by ~sHyLoCk~ on 2009-06-14
> **blueridgedog said:**
> Can you specify "gnome-terminal" as an application using the menu you mentioned?

Yes that works for me!

---

### Post by pat13nc3 on 2009-06-14
Worked like a charm

At first I tried just browsing to the shortcut on the desktop...
That didn't work very well
By very well I mean at all

Now I don't have to open terminal every time I log on

Thanks everybody!

---

### Post by gamblor01 on 2009-06-14
I'm not sure what System > Preferences > Startup Applications does (I'll have to try it right now) but you can also create the file .gnomerc in your home directory and add any commands you want into that file.  Assuming it doesn't exist, you could just echo the command you want and redirect it into the file:

```

echo "gnome-terminal &" > ~/.gnomerc

```

of course if the file already exists (or you don't want to redirect output) you can always edit it with your favorite editor, such as gedit and then put your commands in there:

```

gedit ~/.gnomerc

```

I'm going to check right now but I wonder if the Startup Applications menu option just inserts stuff into .gnomerc for you.  ;)

---

### Post by gamblor01 on 2009-06-14
Weird...I don't even have an option called "Startup Applications" on my System -> Preferences menu.  It's not under System -> Administration either.  I'll just stick with manually editing my .gnomerc I guess...

---

### Post by pat13nc3 on 2009-06-14
Hey thanks gamblor01,
Although the Startup Applications worked for me,
I honestly prefer to do things through a terminal

I tried opening the file and I found it,
So next time I need to add a startup program
I'll try your method
Thanks!

---

### Post by pat13nc3 on 2009-06-14
Hey gablor01,
what version of Ubuntu are you running?

I'm using 9.04, if you're profile is accurate (8.10)
Then I think the same thing is located at
System > Preferences > Sessions
And then there's a tab for Startup Programs.

If you're interested in the graphical version, that is,
Though what you're doing should work fine

---

### Post by ~sHyLoCk~ on 2009-06-15
> **gamblor01 said:**
> Weird...I don't even have an option called "Startup Applications" on my System -> Preferences menu.  It's not under System -> Administration either.  I'll just stick with manually editing my .gnomerc I guess...

But it's there by default, atleast it's in jaunty and I'm pretty sure it was in previous ones as well. :O

---

### Post by gamblor01 on 2009-06-16
> **pat13nc3 said:**
> Hey gablor01,
what version of Ubuntu are you running?

I'm using 9.04, if you're profile is accurate (8.10)
Then I think the same thing is located at
System > Preferences > Sessions
And then there's a tab for Startup Programs.


You're right...it looks like they moved it in 9.04.  The menu is indeed located under System -> Preferences -> Sessions in 8.10.

No matter, the terminal works just fine and is much more flexible anyway.  ;)

---


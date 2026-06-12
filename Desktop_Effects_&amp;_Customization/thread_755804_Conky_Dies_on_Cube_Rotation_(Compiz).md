---
title: "Conky Dies on Cube Rotation (Compiz)"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by becatlibra on 2008-04-15
Does anyone have experience using Conky with Compiz?  I have the 'Advanced Desktop Effects Settings' option installed and have tuned it down to just use the Desktop Cube Rotation - However, sometimes, when I rotate the cube (or if I just click my desktop) Conky dies.  

I don't understand what is happening.  It is simply a text overlay.  I have already had to writeup a start script to delay it when called (on startup).  

Does anyone have any suggestions?

Thanks,

Benjamin

---

### Post by +++ IGOR +++ on 2008-04-16
I had the same problem. For me it was that conky was started before nautilus. By using a script to load conky AFTER nautilus had started I was able to use it without problems.

write this in a file:
#!/bin/sh

  sleep 10
  conky &
  fi


After you have done this you set the file to be executable and add it to "sessions" so that it is started as X starts.

What this script does is that it tells conky to wait so that it starts after nautilus, I have rather slow loading of X so i use "sleep 20" so that I know that conky starts after nautilus.

I hope this solves your problem.

---

### Post by Zorael on 2008-04-16
> **becatlibra said:**
> I have already had to writeup a start script to delay it when called (on startup).

> **+++ IGOR +++ said:**
> What this script does is that it tells conky to wait so that it starts after nautilus, I have rather slow loading of X so i use "sleep 20" so that I know that conky starts after nautilus.

I hope this solves your problem.

:>


Anyway. To rule out you having the delay set too low, what happens if you manually start Compiz first and then Conky, instead of having them run automatically upon login?

```
$ killall conky
$ metacity --replace &
$ compiz --replace &
$ conky &
```

---

### Post by Ardent Maverick on 2008-04-24
I have this same problem, and can add these details:

1.) When Conky disappears, it has gone *behind* the desktop.  (I know this because I have the desktop set to transparent in Compiz' settings.)

2.) I have the .conkyrc variable "own_window_type = desktop" as opposed to 'normal' or 'override.'  I heard this one helped Conky to behave best with Ubuntu and Compiz.

3.) I also have a stickynote open on my desktop, and when I click on my desktop not only does Conky 'disappear', but also the stickynote minimizes.  (Unsure if this is related.)

I'm also looking for a solution.

---

### Post by becatlibra on 2008-05-01
I hate doing this but I have this same problem as well - I am using a sleep script, etc.  Compiz, was Gutsy now Hardy.  When the desktop is clicked it goes away (or rather is behind).

Any word?

Regards,

B

---

### Post by vikasvishnu on 2008-05-02
> **becatlibra said:**
> I hate doing this but I have this same problem as well - I am using a sleep script, etc.  Compiz, was Gutsy now Hardy.  When the desktop is clicked it goes away (or rather is behind).

Any word?

Regards,

B

When Conky dies, take a gnome-terminal and give the command 'conky' and dont close the terminal. Then do what ever you used to do and when Conky dies, take a look at the terminal. It should show you the reason or atleast some errors which you can post here for us to troubleshoot. 

I totally believe that it must be something with your .conkyrc file in your home directory. Just try using a new .conkyrc file (you can collect many of them from gnome-look.org) and see if the problem persists.

-:Vikas:-

---


---
title: "can't get into os folder"
date: 2009-06-14
forum: General Help
---

### Post by obvious_hat on 2009-06-14
I want to get into my OS folder which holds all of the files available. Until recently I have been accessing my media items from this folder, this ended when it no longer allowed me to get into the folder. I have had a look inside the properties of the folder and then permissions. Inside the tab there are no defined permissions. I think this could be the problems. So if someone could help me to get inside it I would be grateful. 
Thanks in advance :D

---

### Post by Amilo1718 on 2009-06-14
did you try 'sudo nautilus' ?

---

### Post by nothingspecial on 2009-06-14
> **Amilo1718 said:**
> did you try 'sudo nautilus' ?


That would be ```
gksudo nautilus
```

sudo for command line

gksudo for graphical apps

Click on properties and try again

---

### Post by obvious_hat on 2009-06-14
> **Amilo1718 said:**
> did you try 'sudo nautilus' ?

yeah, nautilus doesn't like the computer folder, it seems

---

### Post by nothingspecial on 2009-06-14
```
ls -l /path/to/os_folder
``` to see permisions

---

### Post by obvious_hat on 2009-06-14
> **nothingspecial said:**
> ```
ls -l /path/to/os_folder
``` to see permisions

this doesn't seem to be working, could just be my general newbiness to ubuntu

---

### Post by nothingspecial on 2009-06-14
Where is your os folder?

---

### Post by obvious_hat on 2009-06-14
> **nothingspecial said:**
> Where is your os folder?

it's in the computer folder, it's the other partition that isn't ubuntu

---

### Post by ajgreeny on 2009-06-14
> **nothingspecial said:**
> Where is your os folder?
And what exactly do you mean by os folder?  Perhaps you mean "File system" in the nautilus *Places* or *Tree* layout in the left hand pane.

---

### Post by nothingspecial on 2009-06-14
> **obvious_hat said:**
> it's in the computer folder, it's the other partition that isn't ubuntu

Is that a "windows" partition?

---

### Post by obvious_hat on 2009-06-14
> **ajgreeny said:**
> And what exactly do you mean by os folder?  Perhaps you mean "File system" in the nautilus *Places* or *Tree* layout in the left hand pane.

no file system works fine, it's the folder os that doesn;t allow me to mount the volume, would screenshots help?

---

### Post by obvious_hat on 2009-06-14
> **nothingspecial said:**
> Is that a "windows" partition?

yes, it is

---

### Post by Amilo1718 on 2009-06-14
> **nothingspecial said:**
> That would be ```
gksudo nautilus
```

sudo for command line

gksudo for graphical apps

euhm srry to correct you... but that's not valid anymore for nautilus on jaunty....

---

### Post by nothingspecial on 2009-06-14
See [[COLOR="Red"]here[/COLOR]]("http://www.psychocats.net/ubuntu/mountwindowsfstab")

and [[COLOR="Blue"]here[/COLOR]]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by nothingspecial on 2009-06-14
> **Amilo1718 said:**
> euhm srry to correct you... but that's not valid anymore for nautilus on jaunty....

Ok, but then lots of linux users use these forums and not everyone is using jaunty. But point taken.

.....I seem to have used use alot.....

---

### Post by ajgreeny on 2009-06-14
> **Amilo1718 said:**
> euhm srry to correct you... but that's not valid anymore for nautilus on jaunty....
What's not valid anymore?  I still use it occasionally.  I accept that it is not necessary now with the *nautilus-gksu* extension, but it does still work.

---

### Post by Amilo1718 on 2009-06-14
> **ajgreeny said:**
> What's not valid anymore?  I still use it occasionally.  I accept that it is not necessary now with the *nautilus-gksu* extension, but it does still work.

it works... but it's not needed anymore
my bad... wrong choice of words (can be disastrous in a *nix environment, i know)

---


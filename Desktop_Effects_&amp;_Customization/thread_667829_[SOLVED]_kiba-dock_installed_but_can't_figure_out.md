---
title: "[SOLVED] kiba-dock installed but can't figure out"
date: 2008-01-14
forum: Desktop Effects &amp; Customization
---

### Post by xfearxnxloathing on 2008-01-14
i installed kiba-dock by downloading a script, making it executable and typing in some commands in the terminal to install.  funny things i get this message and i do not know how to do what it is asking.  please help guys!

> Kiba-dock is installed now!   To run Kiba-dock, you must execute 'kiba-dock'

i swore i installed kiba-dock way easier a few months back...

---

### Post by Casual Fan on 2008-01-14
Just type kiba-dock in a terminal.

---

### Post by xfearxnxloathing on 2008-01-14
> **Casual Fan said:**
> Just type kiba-dock in a terminal.

do i have to be in the directory i installed to?

> atreyu@aXion:~$ kiba-dock
bash: kiba-dock: command not found

---

### Post by Casual Fan on 2008-01-14
Why did you go to the terminal to download kiba dock originally? It's available in synaptic.

First, go to system>administration>software sources and on the Ubuntu software tab, make sure all the boxes are checked.

Then, go to system>adminstration>synaptic package manager. Search for kiba-dock. Right click on it and select "mark for installation" and then apply.

Kiba-dock will then appear as a menu choice under Applications>accessories. 

Works like a charm.

---

### Post by santiagoward2000 on 2008-01-14
> **Casual Fan said:**
> Why did you go to the terminal to download kiba dock originally? It's available in synaptic.

First, go to system>administration>software sources and on the Ubuntu software tab, make sure all the boxes are checked.

Then, go to system>adminstration>synaptic package manager. Search for kiba-dock. Right click on it and select "mark for installation" and then apply.

Kiba-dock will then appear as a menu choice under Applications>accessories. 

Works like a charm.

Hi!
I'm sorry to contradict you, but Kiba is not on Ubuntu's repositories. As you are using Feisty, I assume you have added Treviño's repository, and that's why you have it.

---

### Post by xfearxnxloathing on 2008-01-14
> **Casual Fan said:**
> Why did you go to the terminal to download kiba dock originally? It's available in synaptic.

First, go to system>administration>software sources and on the Ubuntu software tab, make sure all the boxes are checked.

Then, go to system>adminstration>synaptic package manager. Search for kiba-dock. Right click on it and select "mark for installation" and then apply.

Kiba-dock will then appear as a menu choice under Applications>accessories. 

Works like a charm.

i'll try this in a little while, the wife comes first unfortunately. :wink:

---

### Post by Casual Fan on 2008-01-14
> **santiagoward2000 said:**
> Hi!
I'm sorry to contradict you, but Kiba is not on Ubuntu's repositories. As you are using Feisty, I assume you have added Treviño's repository, and that's why you have it.

What, you're just going to contradict me but not tell our friend how to add the repository?

:rolleyes::)

Okay, open up that software sources window again.
Click on third-party software tab.
Click on add.
Paste ```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
``` into the box.
Click on Add Source.
Click on Close.
Click on Reload.
THEN, go search for kiba-dock like before.
Works like a charm!:lolflag:

---

### Post by xfearxnxloathing on 2008-01-14
> **Casual Fan said:**
> What, you're just going to contradict me but not tell our friend how to add the repository?

:rolleyes::)

Okay, open up that software sources window again.
Click on third-party software tab.
Click on add.
Paste ```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
``` into the box.
Click on Add Source.
Click on Close.
Click on Reload.
THEN, go search for kiba-dock like before.
Works like a charm!:lolflag:

i actually do not use fiesty, i'm using gutsy.  what software sources should i be using?

---

### Post by Casual Fan on 2008-01-14
This works for Gutsy too.

---

### Post by santiagoward2000 on 2008-01-15
> **Casual Fan said:**
> What, you're just going to contradict me but not tell our friend how to add the repository?

:oops: Sorry about that! I'll try to be more considerate next time!

> **Casual Fan said:**
> This works for Gutsy too.

Are you sure about this? I haven't tried using Treviño's repositories for Feisty on Gusty, but I read this caused many problems...
I installed Kiba-Dock using this guide here:
[http://ubuntuforums.org/showthread.php?t=554127]("http://ubuntuforums.org/showthread.php?t=554127")
(You've got to do a little more work than using a repository, but it works perfectly)
I hope this helps you!
Cheers!

---

### Post by xfearxnxloathing on 2008-01-15
> **Casual Fan said:**
> This works for Gutsy too.

it totally showed up in the package manager i selected it and applied, it installed and resides under Applications>Accessories, thnx!!!:guitar:

---

### Post by Casual Fan on 2008-01-15
> **santiagoward2000 said:**
> :oops: Sorry about that! I'll try to be more considerate next time!

I'm just teasing! :)

---

### Post by santiagoward2000 on 2008-01-16
> **Casual Fan said:**
> I'm just teasing! :)

I know that! No problem! :biggrin:

---


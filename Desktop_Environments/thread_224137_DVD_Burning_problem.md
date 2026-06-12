---
title: "DVD Burning problem"
date: 2006-07-27
forum: Desktop Environments
---

### Post by Zombithium on 2006-07-27
Hi,
I have just installed dapper. I was trying to burn a DVD using the default DVD burning software that comes with ubuntu.
The problem is that whenever i try to burn a disc, it shows an error stating that not enought space present for the selected image. 
I guess that it is using /tmp for creating a temporary copy of the files and then it tries to burn. My problem with this is that i have only 3.0GB for ubuntu (out of which only 800MB is free) and i am trying to burn files from my windows partition.
So is the error because of lack of space on the ubuntu partition?
Is there any way to bypass this problem? may be some other software which does't need so much space..?

thanks.

---

### Post by kazuya on 2006-07-27
I am tempted to suggest gnomebaker. If space was not such a big deal, I would recommend k3b over any other for CD or DVD burning. It is very similar to nero for windows, but more powerful in my experience. It is a KDE application though, but it runs automatically in gnome environment as well.

K3b is the way.

You may get k3b through synaptic. Or sudo apt-get k3b     
Look out for what else may get installed with k3b though if space is a concern.

---

### Post by greenstar on 2006-07-27
> **Zombithium said:**
> Hi,
I have just installed dapper. I was trying to burn a DVD using the default DVD burning software that comes with ubuntu.

If you want help with an application, we need to know the name of the app your using. Are you using nautilus to burn your DVDs? I can't think of anything else that comes with the Ubuntu installation. You have to apt-get gnomebaker & graveman.

However, this isn't even the biggest problem. You said yourself:


> **Zombithium said:**
> 
The problem is that whenever i try to burn a disc, it shows an error stating that not enought space present for the selected image. 
I guess that it is using /tmp for creating a temporary copy of the files and then it tries to burn. My problem with this is that i have only 3.0GB for ubuntu (out of which only 800MB is free) and i am trying to burn files from my windows partition.

Let's solve this problem with some simple arithmetic. 

Q. How many times can 4.35Gb of data go into 800Mb of space? 
A. Zero (less than one)  800/4472 = 0.18

> **Zombithium said:**
> 
So is the error because of lack of space on the ubuntu partition?

Absolutely this is the problem.

> **Zombithium said:**
> 
Is there any way to bypass this problem? 

With a larger partition. Any OS that you'll be using to burn DVD's is going to need at least 4500MB of free disk space just to store the temp image of a full DVD. This is regardless of what OS or burning app you use.

> **Zombithium said:**
> 
may be some other software which does't need so much space..?

The application you choose to burn with has no relationship to the size of the data to be burned. Changing burning apps is not going to fix this problem, repartitioning your disk will.

If you don't have enough disk space to store a temporary copy of whatever you're burning, then you're not gonna be able to burn it.

Hope this helps,
Greenstar

---

### Post by Hezekiah on 2006-07-27
There are applications which can burn directly to a CD/DVD without creating a temporary image first - I don't know which apps work in which way though.

Definitely try k3b if you are able, as it is currently the most capable of the available burning programs.

---


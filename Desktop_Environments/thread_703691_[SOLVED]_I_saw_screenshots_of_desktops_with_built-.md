---
title: "[SOLVED] I saw screenshots of desktops with built-in terminals..."
date: 2008-02-21
forum: Desktop Environments
---

### Post by Pogeymanz on 2008-02-21
I can't find a pic now, of course. But, it looked just like a normal desktop pic, except that right in the middle of the desktop it had "name@ubuntu:~$:"

I want that! Can I do that with XFCE4? I would love to just click over to a clean desktop to type a command instead of openning a terminal. (Even though I pimped my terminal out)

---

### Post by bwhite82 on 2008-02-21
sudo apt-get install tilda

or

devilspie

---

### Post by imoatama on 2008-02-21
I have that under gnome, not sure if you can achieve it the same way under xfce though. I'm pretty sure it's what you saw the screenshot of though - tilda is a drop-down terminal afaik.

For what it's worth though you can find [instructions here]("http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html")

---

### Post by waldorsockbat on 2008-02-21
> **imoatama said:**
> I have that under gnome, not sure if you can achieve it the same way under xfce though. I'm pretty sure it's what you saw the screenshot of though - tilda is a drop-down terminal afaik.

For what it's worth though you can find [instructions here]("http://www.ubuntu-unleashed.com/2007/08/howto-completely-transparent-shell-on.html")


Thanks for the link,been looking for info on how to do this.

---

### Post by dse.37 on 2008-02-22
It can also be done by setting up a new terminal profile with certain properties and compiz.

I've added a text file with the instructions. I'm sorry I can't point to a source as I've forgot where I had it from. It works well though.

---

### Post by bwhite82 on 2008-02-23
> - tilda is a drop-down terminal afaik.

It can be configured to be persistent, and borderless, and scrollbarless, etc. Or you can configure it to dropdown via the tilde key.

-Cheers

---

### Post by santiagoward2000 on 2008-02-23
> **EmosSuck777 said:**
> I can't find a pic now, of course. But, it looked just like a normal desktop pic, except that right in the middle of the desktop it had "name@ubuntu:~$:"

I want that! Can I do that with XFCE4? I would love to just click over to a clean desktop to type a command instead of openning a terminal. (Even though I pimped my terminal out)

Hi!
Actually, in Xfce it's even easier than in Gnome, because xfce4-terminal already has the option to remove window borders.
To do it, open a terminal, go to **Edit/Preferences**. Under **General**, there's a dropdown menu at the bottom that says: **Scrollbar is:**. Click on it and select **Disabled**.
Then, go to **Appearance** and in **Background** select **Transparent background** and move the bar to **None**.
Finally, still under **Appearance**, uncheck **Dislay menubar in new windows** and **Display borders around new windows**.
That's it. Next time you open a terminal it'll be the way you want it.
Just in case you need to move it, you can press Alt and drag it.
Cheers!

---

### Post by Pogeymanz on 2008-02-24
Great. But how can I go in and change all the stuff back to normal if I change my mind?

---

### Post by santiagoward2000 on 2008-02-24
> **EmosSuck777 said:**
> Great. But how can I go in and change all the stuff back to normal if I change my mind?

You can enter to **Preferences** by right-clicking on the terminal. With the right-click menu you can also enable **Show Menubar**, and enter **Preferences** as you did before. Then, all you have to do is set the options back.
Cheers!

---

### Post by mtbsoft on 2008-02-27
I use the Terminal screenlet to achieve this (below, 60% opaque, sticky), perhaps that would do for you too?

---


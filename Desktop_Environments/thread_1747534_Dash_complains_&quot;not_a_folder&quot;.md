---
title: "Dash complains &quot;not a folder&quot;"
date: 2011-05-02
forum: Desktop Environments
---

### Post by shochatd on 2011-05-02
Starting today, I have a new problem with "Files & Folders". No matter what file I click on, I get the same error message. For example, "**Could not display "/work/photos/2011/March_LA/DSC_1585.JPG" The location is not a folder.**"
Of course it's not a folder, since it is obviously an image file. If I navigate to this same file via Nautilus and double-click, it is opened properly. Is there some way to reset everything Unity back to some sort of default state? The only thing I did recently was to uninstall Thorin (XFCE file manager) which I had previously said to use for folders selected in the Dash. By the way, actual folders now work fine (and come up in Nautilus), but it now thinks everything is a folder. It doesn't make any difference what kind of file (.JPG, .mp4, .gnumeric,...) always the same "not a folder" error.

---

### Post by shochatd on 2011-05-02
I went back to Synaptic and removed all traces of XFCE. I thought I had already done that, but I had not. Now the problem has disappeared and everything is working properly. .jpg's come up in eog, .gnumeric's come up in gnumeric, etc. And folders come up in Nautilus. The way I figured out that it was XFCE-related was that when I went into another user account, clicked a .jpg in the Dash, and again got that dialog asking what my preferred file manager for the Dash was, I tried choosing "other". And it said something like "Choose preferred file manager for XFCE". XFCE! So somehow, the mere presence of XFCE on the system can cause Unity to malfunction.

---

### Post by edgreenberg on 2012-01-13
I had the same problem, with Gnome, not Unity, on 11.04.  Firefox and most apps would return "location is not a folder" but Nautilus would open them fine.  On the strength of this thread, I removed all traces of xfce with 

sudo apt-get remove `dpkg -l | grep xfce|awk '{print $2}'`

and the problem is resolved.  

I had hoped to try out xfce, but not at the expense of Gnome. 

Thanks for the posts.

---

### Post by theseekerwho on 2012-01-26
> **edgreenberg said:**
> I had the same problem, with Gnome, not Unity, on 11.04.  Firefox and most apps would return "location is not a folder" but Nautilus would open them fine.  On the strength of this thread, I removed all traces of xfce with 

sudo apt-get remove `dpkg -l | grep xfce|awk '{print $2}'`

and the problem is resolved.  

I had hoped to try out xfce, but not at the expense of Gnome. 

Thanks for the posts.

This worked perfectly for me, merci.

---


---
title: "Command to open Home Directory in Nautilus with search function?"
date: 2022-04-11
forum: Desktop Environments
---

### Post by grxgghxrpxr on 2022-04-11
Hi everyone, I hope you are doing well.

I am looking to create a shortcut for the search key on my laptop keyboard. I would like to open the Home directory in Nautilus, then open a search at the same time (so I can just press that & type what I need to to find the files in my Home folder). 

Is there any command I can use to create this shortcut?

Thank you, I'd really appreciate it,
Gregg.

---

### Post by TheFu on 2022-04-11
IDK, but what would you type (don't use the mouse) to make this happen?  Using xdotool, you can assign a key to run any command/script.

With some DEs, you can tap the **Super** key, then start typing any filename ... then hit <enter> as the file is selected as more and more are removed with each character. No need for the extra step of a file manager.

---

### Post by grxgghxrpxr on 2022-04-11
I understand that, and thank you for the suggestion.

But I was writing this post to see if there was specficially a command to open a directory then turn on the search function in Nautilus.

---

### Post by TheFu on 2022-04-11
Did you check the Nautilus manpage (aka Gnome-Files) help online?
[http://manpages.ubuntu.com/manpages/focal/en/man1/nautilus.1.html](http://manpages.ubuntu.com/manpages/focal/en/man1/nautilus.1.html)   I just did. Perhaps you have a different OS release that has different options and could work? There doesn't seem to be any mention of 'search' there, but perhaps I missed it?

I think using **xdotool** or just use a dedicated search tool, are the only real options.   There must be 15 search tools.  [http://manpages.ubuntu.com/manpages/bionic/man1/gnome-search-tool.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/gnome-search-tool.1.html) is one. It accepts a directory to search AND query terms. I think it could meet your needs, but only you can check it out. I don't have it on any of my systems and it isn't offered as an option.

I like **Recoll** because it is basically google for my storage, but it needs daily indexing to keep current. I find the Recoll GUI much to fat/bloated for searching, but the CLI interface is very fast and returns relevant results in less than 1sec with lots of options possible - like soundex. I'm terrible at spelling, so soundex finds results that can be spelled very different, but the sounds are close. Also, it knows to ignore word endings.  Ah ... Recoll looks inside files, not just at the filename.  When I want to only search filenames, I use **locate**.

Lots of possibilities.

---

### Post by philhughes on 2022-04-12
If a understand correctly what you want to do, then the following should work:

Settings > Keyboard > Customise Shortcuts

Click Custom Shortcuts > Add Shortcut

Add

Name: (whatever)
Command: nautilus -w
Shortcut: (whatever key combo you want)

Now when you press that key combination, a new nautilus window will open with your Home directory selected, and you just need to start typing to activate the search function.

---

### Post by TheFu on 2022-04-12
But that won't automatically bring up the search.
With xdotool and a tiny script can be tied to a keypress: 
```
nautilus ~  ; sleep 1s; xdotool key --clearmodifiers C-f
```
this assumes that <cntl>-f will bring up the search dialog and that the window manager sets a new window to have focus.  Not the way my setup is, but I suspect most people work that way.  IDK.

I did test this with caja. The C-f didn't work even when the window focus was correct. That seems odd, since I use it lots of other places.  

I suppose a short **cnee** script could work.  That tool is extremely positionally sensitive, so placement of the nautilus window and the geometry would likely be required. Something like: **caja -g 600x400 &** OTOH, it sends exact mouse and keyboard inputs, so it will work.  The workflows I have it automating are usually 5-10 minutes long.  cnee probably doesn't work with Wayland. It is an X/Windows tool, but so is xdotool. But IDK about recent Wayland. Last time I looked was about 2 yrs ago and it didn't work.

---

### Post by vanadium on 2022-04-13
It is already working out of the box like that. Open Files. You can immediately start typing and search will begin.

---

### Post by tea for one on 2022-04-13
> **vanadium said:**
> It is already working out of the box like that. Open Files. You can immediately start typing and search will begin.

That is a revelation.
Even for those of us who have used Nautilus/Files for many years, there is always something to learn.

Thanks for the tip.

---

### Post by grxgghxrpxr on 2022-04-23
God I feel so stupid now lmao.

Thank you so much.

---


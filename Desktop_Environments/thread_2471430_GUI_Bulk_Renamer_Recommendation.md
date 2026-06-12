---
title: "GUI Bulk Renamer Recommendation"
date: 2022-01-30
forum: Desktop Environments
---

### Post by erosman on 2022-01-30
re: Ubuntu 21.10

I have been looking at GUI bulk renamers to rename file/folder with RegEx capability.

On Windows I use RegexRenamer which is only 1.6mb.

'Smart File Renamer' seems to be 93mb :o

Some apps appear to require changes to Gnome e.g. Thunar, KRename

Some are no longer on apt-get e.g. pyRenamer, GPRename

---

### Post by TheFu on 2022-01-30
I use **qmv**. It opens a paired list of filenames (original   new) in my editor of choice (vim) and I can search and replace like a boss.
Sometimes I want just a list to make as the "new" - **qmv -fdo** does that.  Just don't remove any lines or change the order.
The GUI is up to you, since it will be your editor.  Set the EDITOR environment variable in your .bashrc and all sorts of tools will honor that - visudo, sudoedit, qmv .... the list goes on and on.  vim has the ability to perform rectangle cut/pasting along with smart numbering for all sorts of objects - numbers, days, months, and user-defined lists. For renaming media files, qmv rocks completely.

For photos, **geeqie** has a bulk renamer.  I stopped using it since learning about qmv. It was too much hassle compared to using my most-awesome editor.

Not a GUI, but if you need to rename 100K files, the perl too 'rename' does sed-like regex (actually the full perl RE) which means nearly unlimited capabilities at our fingers. Probably not what you seek.

I've seen a few file manager extensions mentioned in these forums over the years just for renaming.  Since I don't really use any file managers, I didn't follow too closely. Think they were written in python to integrate into Nautilus (aka Files on Gnome-running Ubuntu).

Have you checked alternativeto.net for options?

---

### Post by schragge on 2022-01-30
To clarify: **qmv** is part of package **renameutils**.

---

### Post by ActionParsnip on 2022-01-31
[https://www.omgubuntu.co.uk/2010/08/batch-rename-files-in-ubuntu-with-renamer](https://www.omgubuntu.co.uk/2010/08/batch-rename-files-in-ubuntu-with-renamer)

---

### Post by schragge on 2022-01-31
> **erosman said:**
> re: Ubuntu 21.10
[...]
Some are no longer on apt-get e.g. pyRenamer, GPRename
GPRename is still [there](https://packages.ubuntu.com/impish/gprename).

---

### Post by erosman on 2022-02-01
Thank you for the suggestions.[B]

qmv [/B]appears to be CLI while I am looking for GUI.

> Renamer is a small app for batch renaming files in nautilus, with a  simple yet intuitive gtk+ interface and  lots of options and features.   This app can also be purchased in Ubuntu Software Center.
I am looking for free (preferably open-source) software.

[s]**GPRename** seems to have been removed from 21.10[/s]

I am trying **FileRename** which is only 2mb.

---

### Post by schragge on 2022-02-01
> **erosman said:**
> **GPRename** seems to have been removed from 21.10
Have you clicked on the link in [post=14078567]my previous post (#5)[/post]?

---

### Post by TheFu on 2022-02-01
> **erosman said:**
> Thank you for the suggestions.[B]

qmv [/B]appears to be CLI while I am looking for GUI.

will use whatever editor you like. Use a GUI editor and it is magically "a GUI" program.

---

### Post by erosman on 2022-02-02
> **TheFu said:**
> will use whatever editor you like. Use a GUI editor and it is magically "a GUI" program.
I am not sure if I understood. I will do some reading on it.

> **schragge said:**
> Have you clicked on the link in [post=14078567]my previous post (#5)[/post]?


You are correct..... my mistake
It is only 5mb (with additional libs).
I will try it.
I have installed it but it doesn't appear in Activities and the search doesnt show it !?
```
sudo apt-get install gprename
```
When trying to re-install it says
```
gprename is already the newest version (20201214-0.1).
```


**Update:** I found out that I can launch pgrename from the terminal. Is that the right way?

---

### Post by TheFu on 2022-02-02
> **erosman said:**
>  
**Update:** I found out that I can launch pgrename from the terminal. Is that the right way?

You can run **any** program from a terminal.  Whether it is useful or not is really the question.  
If a program isn't working the way you expect, running it from a terminal will let you see the different output messages. This can be very helpful.

---

### Post by erosman on 2022-02-03
Thank you. I meant GPRenamer installation doesn't have any desktop icon so the only way I can see is to launch from terminal OR create a .desktop manually.
GPRenamerhas a weird Regular Expression implementation regarding backreference. Without a good Regex, the built-in Ubuntu Nautilus rename function does most of what is needed.
Furthermore, the highlighted file list on the left pane is black text on black background (on light theme) so it becomes invisible. It looks OK on Dark theme.

---


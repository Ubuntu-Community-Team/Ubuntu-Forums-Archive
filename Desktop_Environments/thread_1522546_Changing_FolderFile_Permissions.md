---
title: "Changing Folder/File Permissions"
date: 2010-07-02
forum: Desktop Environments
---

### Post by crazy dave on 2010-07-02
Hi,

It seems it is impossible to easily change folder permissions in the 10.04 GUI.  I wanted to move a folder and its contents to another usr and changed its permissions (and the enclosed files) but the GUI under 'Users and Groups' changing the folder ownership(user and group) and clicking 'apply to enclosed files' simply changes the permissions of the folder but not the enclosed files.  As this folder contains hundreds of files, you would expect it to thake a minute or so to change the permissions of the enclosed files but nothing happens.

I know there is chmod in terminal but id the GUI is ther surely it should work? you can't easily navigate to different folders in terminal and look at their properties unless you can remember all of those folder paths.

Any relevant advice would be appreciated.

---

### Post by clrg on 2010-07-02
Maybe you cannot change the subfolder's permissions because you don't have the right to do so. For example, I cannot change the ownership of a file of mine to root:root. Only root can do that. Also, I can't change the permissons of another user's files.

Since Nautilus is running under your username.. you get the idea. You may elevate Nautilus' permission level by pressing Alt+F2 and typing "gksudo nautilus". However, I recommend you use the terminal.

---

### Post by iponeverything on 2010-07-02
> "gksudo nautilus". However, I recommend you use the terminal.

I think that your are probably right @clrg in that he might need to sudo first. I disagree that using the terminal might be better. A simple space in the wrong place for a recursive chmod has caused more that its fair share heartaches here..

---

### Post by clrg on 2010-07-02
> **iponeverything said:**
>  A simple space in the wrong place for a recursive chmod has caused more that its fair share heartaches here..

That's why no one (should) ever run a potentially destructive command with root permissions without double-checking it. </smartass>

A colleague of mine found a bug in Nautilus. Guess what? He ran it as root, wanted to change the permissions of a file in /usr/share... Result? Nautilus chmod'd random files to 400, which isn't that cool either (reinstallation was necessary).

---

### Post by iponeverything on 2010-07-03
> That's why no one (should) ever run a potentially destructive command with root permissions without double-checking it. 

For someone that is not familiar with paths, special characters and command line syntax, double-checking is not going be to too useful. While I would absolutely love it if everyone would at least the basics of command line filesystem navigation, basic file operations and process management.. It is never going to happen. 

> A colleague of mine found a bug in Nautilus. Guess what? He ran it as root, wanted to change the permissions of a file in /usr/share... Result? Nautilus chmod'd random files to 400, which isn't that cool either (reinstallation was necessary).

If you can't trust Nautilus, what can you trust ;) Personally I prefer the command line, I am just aware of this because of two threads here in past week where some mucked there systems because of misplaced space.

---

### Post by crazy dave on 2010-07-03
> **clrg said:**
> Maybe you cannot change the subfolder's permissions because you don't have the right to do so. For example, I cannot change the ownership of a file of mine to root:root. Only root can do that. Also, I can't change the permissons of another user's files.

Since Nautilus is running under your username.. you get the idea. You may elevate Nautilus' permission level by pressing Alt+F2 and typing "gksudo nautilus". However, I recommend you use the terminal.

Maybe I should have mentioned that I was root when trying to do this, but I thought that was implied given that if I was trying to change root:root as a desktop user the particular files would carry the 'x' icon and the GUI drop-downs to 'try' to change the user and group would be 'grayed out'.  Its only after changing the dropdown options that anyone would then click on the 'apply permissions to enclosed files' option.  In fact this option is not avaialable if you are not root when trying to change a root access folder.

Also, if I wasn't root then how would the folder permissions have changed but not the permissions of the enclosed files.

I have searched the forums and there is a sense that the GUI permissions setting function, simply doesn't work properly.  In fact, its easier to change the permissions of a file in Windows, god help us!

---

### Post by Yarui on 2010-07-03
When you say you were root, do you mean you are on the root account (which isn't present by default in Ubuntu) or do you mean you had already elevated your priveleges in nautilus?

Personally I find the command line method of changing priveleges recursively less of a hassle than the GUI method.  It doesn't require you to memorize paths at all, actually.  You can just hit the tab key to autocomplete folder names, and if you don't know the folder name at all you can hit the tab key a few times and it will show the contents of the folder you have typed up to.  If you try to force yourself to do it in the command line a bit more often you will probably get used to it.  I know there are a lot of people who don't really like to do terminal stuff, though, so it is a shame that GUI methods of doing things are sometimes a bit difficult.

> **crazy dave said:**
> I have searched the forums and there is a  sense that the GUI permissions setting function, simply doesn't work  properly.  In fact, its easier to change the permissions of a file in  Windows, god help us!
It is entirely possible that this is correct.  This is a function that a lot of linux users choose to do in the terminal, so I wouldn't be surprised if developers have kind of glossed over this function.

---

### Post by crazy dave on 2010-07-03
> **Yarui said:**
> When you say you were root, do you mean you are on the root account (which isn't present by default in Ubuntu) or do you mean you had already elevated your priveleges in nautilus?

Personally I find the command line method of changing priveleges recursively less of a hassle than the GUI method.  It doesn't require you to memorize paths at all, actually.  You can just hit the tab key to autocomplete folder names, and if you don't know the folder name at all you can hit the tab key a few times and it will show the contents of the folder you have typed up to.  If you try to force yourself to do it in the command line a bit more often you will probably get used to it.  I know there are a lot of people who don't really like to do terminal stuff, though, so it is a shame that GUI methods of doing things are sometimes a bit difficult.


It is entirely possible that this is correct.  This is a function that a lot of linux users choose to do in the terminal, so I wouldn't be surprised if developers have kind of glossed over this function.

Thanks for all of your responses.

I tried it both ways, first by launching nautilus through terminal, sudo nautilus and then by activating the root login and then logging in as root.  In my humble opinion, problems such as these encourage people to activate the root login in order to try to 'sort it out' thereby bypassing the security provided by not having root login activated, but hey.

The fact that developers may have overlooked this is a surprise because it is fundamental and a more natural choice when looking at folder permissions.  I know that Ubuntu is free and open, but this is not a new feature and it still doesn't work?  I've used terminal a lot for instance setting up a VPS on a hosting server because the GUI isn't available, however I've never seen the suggestion that I use terminal for ftp, rather filezilla is the most commonly suggested.

So why people think suggesting Terminal is a solution I don't know, the GUI needs to work sooner or later.

---

### Post by Yarui on 2010-07-03
> **crazy dave said:**
> So why people think suggesting Terminal is a solution I don't know, the GUI needs to work sooner or later.
There is a fundamental flaw in this way of thinking.  This is open source software you are talking about.  I'm not saying your concerns aren't at all important, but the developers of open source software don't develop for others, they mostly develop for themselves.  It's not so much about helping everyone else as it is about making software they want to use themselves.  They are just kind enough to provide their programs to others when they are done with them.  If a feature that you would really like to have has been overlooked time and time again, it's most likely because it's a feature the developers don't really care about.  I understand your frustration, but it's just the price you pay for using open source stuff.

In short, the GUI tool really doesn't NEED to ever work properly.  If you want it to work properly, you may just have to do the work yourself and learn to program a bit.

---

### Post by crazy dave on 2010-07-03
[/QUOTE]In short, the GUI tool really doesn't NEED to ever work properly.  If you want it to work properly, you may just have to do the work yourself and learn to program a bit.[/QUOTE]

I expect that the developers of GNOME would beg to differ with that statement.  Are they working on GNOME 3 under the assumption that it doesn't need to work?

Well given that I am using Ubuntu for a few years now you can tell that I'm a fan.  The reason I personally post issues to the forums is to help bring to light things that could be improved.

As Ubuntu gets better, more users will follow, this will improve the commercial arm and the cloud products.

The permissions not working under the GUI is unfortunately a huge oversight form the end-user's perspective and without end users where would we be ....eh?

---

### Post by Yarui on 2010-07-03
> I expect that the developers of GNOME would beg to differ with  that statement.  Are they working on GNOME 3 under the assumption that  it doesn't need to work?
Well, one feature that is almost never used not functioning correctly  for everyone may be something they don't really care to fix.  Feel free  to submit a bug report or whatever you need to do, they may decide to  fix it, but they may not.  I'm not saying they don't care at all, they  just don't NEED to care, is my point.  Gnome isn't commercial, they aren't making money from the development, so I doubt there is really much motivation to please every single user.

> As Ubuntu gets better, more users will follow, this will improve the commercial arm and the cloud products.
Ubuntu and Gnome are two different things.  The Gnome team doesn't concern themselves with Ubuntu's problems.  I have heard rumors that Canonical wants to find a way to make money from Ubuntu, so I don't entirely disagree that Ubuntu needs to improve if they want to stand a chance as a commercial OS. Like I said, though, I don't really know that they do want to go commercial.  I have just heard rumors, and I don't really care to research it more.  If that is the case, though, this bug is definitely something Canonical should fix if they want users to be satisfied, but again, that doesn't really mean that the Gnome team really needs to fix it themselves.  If users want it that badly they will fix it themselves, the Gnome team is more worried about developing more cutting edge features than worrying about developing tons of GUI tools that most users don't even use.

Like I said, I'm not criticizing your opinion, I understand this kind of stuff can be frustrating, but you need to think from the developer's perspective.  None of them probably use this feature themselves.  They aren't getting paid for their work, so their main motivation to get it done is so they can use it themselves.  They know that a lot of people use their software, so they probably want to include features other users would want even if they don't need them personally, but there is very little demand for this feature.  It probably works properly for some people or surely they would have just removed it completely.

---


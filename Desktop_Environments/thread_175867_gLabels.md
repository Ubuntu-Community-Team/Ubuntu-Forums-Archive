---
title: "gLabels"
date: 2006-05-13
forum: Desktop Environments
---

### Post by georgetoon on 2006-05-13
gLables looks like a really neat little program.  Only thing, I can't import any of my own art files.  The program freezes up. 

I go to create an image object.  I create the area, browse for the file, select the file, and this is where it freezes.  I click okay and nothing happens.  The program freezes.

---

### Post by scooper on 2006-05-14
No idea what the problem is based on the description.  But you could try a couple of things to get more information.  The first is just to run the command from a command line (terminal window).  Sometimes an app displays diagnostic messages that you won't see when you run them from a menu or an icon.  The second level of diagnosis could be to use a program like strace to capture the system calls that are happening.  E.g. from a terminal window run the following:

   strace glabels | tee glabels.out

Obviously you have to make sure strace is installed.  The output may be fairly hard to read, but posting at least the tail end of it may give somebody a better idea of what triggers the freeze.

Another diagnostic could be to check the libraries that are loading.  E.g. run the following at a command prompt:

   ldd /usr/bin/glabels

I think it will show missing libraries or it may show that your using a copy or version that isn't up to date.  Again, posting they output may get you a better answer.

What format are your files?  How big are they?  Anything unusual about them?

Cheers,
Steve

---

### Post by Madpilot on 2006-05-14
This is a known bug with the version of gLabels that's in Breezy. (EDIT to add: here's  [the bug report]("https://launchpad.net/products/launchpad/+bug/1929"), if you're interested)

There's a fairly easy - although slightly risky - fix, though. Because glabels has no particular dependencies, the Dapper version of gLabels will happily run in Breezy - and it doesn't have this image-import bug.

So, edit your sources.list to include the Dapper Universe repo. Start Synaptic, hit Reload, and ignore it when it tells you you have a load of updates. Find gLabels, make sure you're getting the version with the higher number (Dapper's is 2.1.1). Install glabels and glabels-data, then remove the Dapper Universe from your sources.list.

**Remeber to remove the Dapper Universe repo from your sources, and try this for anything but gLabels at your own risk!**

I've been running Dapper's version of glabels for a couple of months now, and it really is a cool app - I even created a template to create CD jewelbox inserts with it.

---

### Post by georgetoon on 2006-05-14
[QUOTE=Madpilot]This is a known bug with the version of gLabels that's in Breezy. (EDIT to add: here's  [the bug report]("https://launchpad.net/products/launchpad/+bug/1929"), if you're interested)

There's a fairly easy - although slightly risky - fix, though. Because glabels has no particular dependencies, the Dapper version of gLabels will happily run in Breezy - and it doesn't have this image-import bug.

So, edit your sources.list to include the Dapper Universe repo. Start Synaptic, hit Reload, and ignore it when it tells you you have a load of updates. Find gLabels, make sure you're getting the version with the higher number (Dapper's is 2.1.1). Install glabels and glabels-data, then remove the Dapper Universe from your sources.list.

**Remeber to remove the Dapper Universe repo from your sources, and try this for anything but gLabels at your own risk!**

I've been running Dapper's version of glabels for a couple of months now, and it really is a cool app - I even created a template to create CD jewelbox inserts with it.[/QUOTE]

Thanks very much.:)  Since I'm still learning about the repositories, I'll just uninstall gLabels and wait to update the entire system to Dapper.:)  For instance, though, ,you write:

> So, edit your sources.list to include the Dapper Universe repo.

Where exactly is that setting in the repositories?  I don't see anything specifically labeled sources.list.  I guess there is some terminology I have to learn. In addition, I don't know what kind of edit is needed. Still new to this.:)

EDIT -- Or am I editing all the packages in the repositories which are labeled "Sources?"  

Thanks again.:)

---

### Post by Madpilot on 2006-05-14
[QUOTE=georgetoon] I don't see anything specifically labeled sources.list.  I guess there is some terminology I have to learn. In addition, I don't know what kind of edit is needed. Still new to this.:)
)[/QUOTE]

Have a look at:
[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

If you wanted to add the Dapper Universe repos, you'd go **Settings->Repositories** in Synaptic, then hit the Add button, then the Custom button, and put "deb [http://archives.ubuntu.com](http://archives.ubuntu.com) dapper universe" in the Apt line.

Make sure this new repository is enabled (check box next to it is checked), then hit the Reload button on Synaptic's main menu bar.

As I said in my first post, ignore Synaptic when it tells you that you've got a pile of updates, and just install gLabels' packages.

Then disable the Dapper Universe repo by just unchecking it in the Repositories window.

"sources.list" is the actual file your repositories settings are kept in; sometimes it's faster to just edit that manually than to mess around in Synaptic's graphical setup tools.

---


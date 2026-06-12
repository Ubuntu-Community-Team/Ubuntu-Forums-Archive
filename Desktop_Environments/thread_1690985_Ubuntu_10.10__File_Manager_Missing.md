---
title: "Ubuntu 10.10  File Manager Missing"
date: 2011-02-19
forum: Desktop Environments
---

### Post by SnoopyDoo on 2011-02-19
Can someone please help!
I have been running Ubuntu 10.10 for a couple of weeks and I now find that if I select Places from the menu and try to open my home or documents folder then the Open Office program would start up and then disappears from the screen with nothing being displayed on the screen.

When I first installed 10.10 the clicking on any folders opened them up showing the files inside the folder.

I looked in the System/Preferences for the File manager as I thought this might of be used to select the method of opening files. However the File Manager is missing in the list.

If it is now a hidden file I do not know how to change this as its normally done through the File Manager.:confused:

---

### Post by w3rt on 2011-02-19
Try doing sudo apt-get install nautilus

---

### Post by Krytarik on 2011-02-19
If you have/see items at your desktop, then Nautilus is definetely running.

I am actually wondering what the mentioned preferences item controls, since Nautilus has its own preferences dialog, and it is completely differrent.

Anytime when you are missing some items in the menus, you can check if they are just hidden by right-clicking at the panel menu and then at "Edit Menus".

However I suppose that your issue is just a inadvertedly misconfigured default handling of the folders.

Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```
Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

---

### Post by okkadiroglu on 2011-02-21
Hi,

I am having some problem with Nautilus too. When I want to open a file with Open With Other Applications option I get a list of software where some software name is repeated many times. When I try to erase some of them I find that the remove button is not highlighted.  I read the help manual and tried to do what is written there but to no avail, somehow I can not remove any duplicate software names form the list opened when Open With Other Applications option is chosen.

Thanks for the help.

Best regards

---

### Post by Krytarik on 2011-02-21
Hi, it would have been great if you had started a new thread on your issue, because this is a completely different one.

However, you are talking about the Wine apps, right? They are also annoying me from time to time. Who would choose "notepad" to open text files?!
You inspired me to search for a solution, and I managed it!:) It's not even that difficult.
- go to "~/.local/share/applications"
- you will find there many files with "wine" at the start of the name
- move those to a backup location, just in case
- done.

Greetings.

---

### Post by okkadiroglu on 2011-02-22
Hi,

Sorry for my misunderstanding. Since this tread is related to Nautilus I took it as a similar problem that I had. 

Many thanks for the help. Sorry, but I am not talking about wine. When I want to open a file Open With Other Applications choice presented in Nautilus menu, a list appears on the screen. In that list, I have many repeating names of softwares that I want to clean. How can I edit available software list in the Open With Other Applications list of Nautilus?

Best Regards

---

### Post by Copper Bezel on 2011-02-22
1. Right-click the file.

2. Select Properties.

3. Select the Open With tab.

4. Remove the items you don't like.

> However I suppose that your issue is just a inadvertedly misconfigured default handling of the folders.

I'm telling you, man, we need a chatbot in here for this question, or maybe just your post as a sticky. Also, we need Nautilus to have an Open With tab for folders. = ) (I can't consider it a "bug" that the default application for folders can be changed, because my desktop has a perfect symbiosis of Thunar and Nautilus folder handling for different situations through that very feature. But it should be more obvious how to change it *back*. = ))

---

### Post by Krytarik on 2011-02-22
@okkadiroglu: The Wine items I mentioned also appear in those list, and in the "Open With..." menu. As I said those of Wine are in your home dir, and there might be others which are also there, but the most are in system-wide "/usr/share/applications", that's why you can't easily remove them.

If you want to remove an item from those menus, you can only move it's respective *.desktop file out of those locations or set the option "Hidden" to "true", which is effectively the same:
[http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#recognized-keys](http://standards.freedesktop.org/desktop-entry-spec/desktop-entry-spec-latest.html#recognized-keys)

So, check first if there are some in your home dir which you no longer need. If there are also system-wide items you want to remove, definetely keep them in a safe location.

@Copper Bezel: Yeah, it's definetely a recurring issue.;-) And the respective option should also definetely be unticked by default. And I can image that it could be not that difficult to build a preferences dialog to change the entries in "mimeapps.list".

---


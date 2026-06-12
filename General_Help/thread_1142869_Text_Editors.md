---
title: "Text Editors"
date: 2009-04-29
forum: General Help
---

### Post by jqp on 2009-04-29
I edit PHP files over an fish/SFTP connection and I'm having trouble finding the best text editor.  I don't have a lot of requirements.  I like Kate's bookmarking, highlighting, wrapping, etc.

Kate - when you type certain things into the Open dialog, it crashes or fails.  For example, typing a relative path like includes/xxx.php will crash it.  In Jaunty, it doesn't even autocomplete filenames when browing a remote directory

Gedit - The Open dialog is even worse.  If you're editing a remote file and pop open the Open dialog, it defaults back to your local home directory.  They've more or less said they won't fix this bug soon.

GPHPEdit - Open dialog is fine, but it's really missing some features.

Any good text editors similar to kate or gedit that don't have these problems?

---

### Post by piratebill on 2009-04-29
for web work I use bluefish.  The save my be a little laggy over ssh, but it works :)

---

### Post by OrganizedFellow on 2009-05-22
Any other recommendations?

I use gEdit with some plugins, but greatly miss Notepad++ on my Win machine.

---

### Post by ad_267 on 2009-05-22
Maybe geany, not sure how well it works with network files though.

> **OrganizedFellow said:**
> Any other recommendations?

I use gEdit with some plugins, but greatly miss Notepad++ on my Win machine.

I just started using Notepad++ again recently when I have to use Windows, and after using vim and gedit on Ubuntu, I'm missing them when I have to use Notepad++. :)

---

### Post by zeroseven0183 on 2009-05-22
I use [**HTML Kit**]("http://htmlkit.com/support/docs/pages/h000134.html"). Neat, light and functional.

---

### Post by OrganizedFellow on 2009-05-22
Thanks fellas.
Someone else recommended SCREEM, which I just downloaded, TOTALLY cool.

This is closer to what I need.
:)

---

### Post by Ms_Angel_D on 2009-05-22
You might want to look into Quanta Plus in add/remove programs it works with remote files.

---

### Post by OrganizedFellow on 2009-05-22
Thanks Ms Angel.
I really liked gedit, because it was a simple simple text editor.
For localhost work, I'll most likely use that, as I've gotten used to its snippets plugin.
For remote, I'll stick with Screen, as it has been a nice new, useful environment ANNND it connects remotely without issues.

I had Quanta and even Bluesfish ... didn't like the 'newb' feel of either one. Too bloated.

Thanks for the recommend though!

---

### Post by jqp on 2009-05-24
I've been using sshfs to mount SSH directories.  That avoids the silly crashing problems I have with Kate.  I need to give Quanta another shot.  It's been a while.

Of course, using sshfs means that reading remote files isn't an issue, but Kate just has some neat things that Gedit doesn't.

Thanks for the replies!

---

### Post by TheMendez1 on 2009-06-07
[FONT=Arial]I use Notepad ++ I find it the best for various reasons:  

1 On the side, it tells you the number of the line
2 It has plug ins
3 For things like HTML you can launch it in a browser directly from Notepad++
4 Lots of other reasons I'm forgetting

Note: if You want to run it, you have to use Wine
[/FONT]

---

### Post by TheMendez1 on 2009-06-07
> **OrganizedFellow said:**
> Any other recommendations?

I use gEdit with some plugins, but greatly miss Notepad++ on my Win machine.

You can still use Notepad++ but, you have to do a few things first

1 Install wine to do that go to System > Administration >Synaptic Package Manager then type in your password look for where it says WINE and install it

2 Download Notepad++ the .bin.zip one extract it to your desktop

3 Then in the terminal change your directory to your desktop

4 Then type in the terminal:  wine ansi/notepad++.exe

---

### Post by piratebill on 2009-07-10
> **OrganizedFellow said:**
> Thanks fellas.
Someone else recommended SCREEM, which I just downloaded, TOTALLY cool.

This is closer to what I need.
:)

Screem is cool, until you try editing any CSS.  Then the program crashes :(

---

### Post by Blacklightbulb on 2009-07-10
eh Pico???

at least it doesn't crash:lolflag:

---


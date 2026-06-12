---
title: "note taking software?"
date: 2009-02-26
forum: General Help
---

### Post by zachthejones on 2009-02-26
I was in class and spied a nearby windows user utilizing a rather interesting piece of software to take notes. Apparently his edition of Microsoft office (which, I belive was one of the latest) came with some sort of "Notes" program designed for taking notes and organizing them.

I was wondering if anyone knew of an open-source (namely linux compatible) program for the same purpose?

Has anyone else out there heard of or used this microsoft product? I was completely unfamiliar with it...I use OpenOffice.org to take notes, but I would love something engineered a little more specifically for note-taking (rather than writing papers).

---

### Post by mb_webguy on 2009-02-27
Tomboy Notes.  It comes with Ubuntu, and can be found in (IIRC) the Applications->Accessories menu.

It organizes things a bit like a wiki.  Every time you type a word or phrase matching a note you've already made, it makes it a link.  And you can organize your notes into different "notebooks".

There are numerous actual wikis for the desktop, but they require you to use certain markup to make the links and such.  Tomboy is more intuitive, if not quite as full featured as some of these others.

---

### Post by latechnissan on 2009-02-27
evernote seems to be a popular note program/website.  I haven't used it personally yet, but you are supposed to be able to take notes with it.

it might be old info but,

[http://abbysays.wordpress.com/2008/05/24/how-to-install-evernote-30-on-ubuntu/](http://abbysays.wordpress.com/2008/05/24/how-to-install-evernote-30-on-ubuntu/)

---

### Post by ubuntu27 on 2009-02-27
I only know three Note taking programs in GNU/Linux:

[LIST=1]
[*][BasKet Note Pads]("http://basket.kde.org/")
[*][Tomboy]("http://projects.gnome.org/tomboy/")
[*][]Wyneken]("http://99b.org/wyneken/")
[/LIST]


I forgot the other one. What was the name of the note taking program for gnome or gtk+ ?

EDIT: I found even more while searching for the one that I had forgotten.
Another list:

[LIST]
[*][Gasket]("http://joey101.net/gasket/")
[*][KeepNote]("http://rasm.ods.org/keepnote/")
[*][NoteFinder]("http://notefinder.co.cc/doku.php")
[*][NoteLab]("http://java-notelab.sourceforge.net/")
[/LIST]

---

### Post by ubuntu27 on 2009-02-27
By the way. If you have a Tablet PC or Tablet Book

You might be interested in the following applications

[LIST]
[*][Xournal]("http://xournal.sourceforge.net/")
[*][Jarnal]("http://www.dklevine.com/general/software/tc1000/jarnal.htm")
[*][Gounal]("http://www.adebenham.com/gournal/")
[/LIST]

---

### Post by linux_tech on 2009-02-27
freemind

---

### Post by zachthejones on 2009-02-28
holy sudo synaptic, batman! Wow, thats a lot of different programs! I'll definitely check 'em out.

I do know of Tomboy and use it regularly, but i don't think it's geared towards taking notes in a class...

If anyone knows of any others feel free to keep the list going. When I've had a chance to check these out I'll post my thoughts on em.

---

### Post by ubuntu27 on 2009-02-28
> **zachthejones said:**
> holy sudo synaptic, batman!

Ha ha ha ha :D I have never seen that kind of expression before. 

From all the note taking applications [BasKet Note Pads]("http://basket.kde.org/") is the most feature rich of them all.
It is in the repository, so you don't need to compile it or download a binary (deb file or others)

---

### Post by zachthejones on 2009-02-28
Thanks so much guys! the Basket Notes one seems to be the closest to what I need. I found KeepNote to be pretty good too, but I think it's more for organizing research notes or something a little more formal.

As it is, Keepnote was the only one which could handle bullets and lists, and I liked its export capabilities as well (claimed capabilities - I never tested them...). I think I'm gonna play with Basket for a bit and see how that turns out. It seems more like a souped up variant of Tomboy.

But I think in the end I'll probably stick with OpenOffice.org word processor for class note taking. I really like the way I can format and use various bullets and lists - none of the programs were quite as intuitive as I need them to be for taking notes in class right now - though if I get quick with the shortcuts, Basket might be close.

I also liked that Basket was in the repos - though it was a slightly older version, it was very easy to install:

```
sudo apt-get install basket
```

Downloaded the .deb install package for KeepNote [here]("http://rasm.ods.org/keepnote/").

And got the package for Gasket [here]("http://pypi.python.org/pypi/gasket/"). The install instructions worked perfectly after extracting the folder - though it did have to download some python stuff to make it work (but it was all automated, so essentially easy). Gasket seemed like a lower powered version of Tomboy - but with some snazzy icons you could insert in the notes pretty easily.

---

### Post by doublewitt on 2009-03-07
Actually, I don't want the older version of Basket Notes. I downloaded the latest .tar.gz file and now I need to know how to install it. The instructions on the website didn't work for me. I wish they could provide a .deb package - that would make it so much easier...!
Anyways, can someone please help me with this?

**OK - I found it**!

---

### Post by zachthejones on 2009-03-07
> **doublewitt said:**
> **OK - I found it**!

Um - where did you find it? I couldn't get the .tar.gz file to work on my laptop either.

---

### Post by doublewitt on 2009-03-08
On this page - *instructions*...
[http://ubuntuforums.org/showthread.php?t=1082112&highlight=install+.tar.gz+files](http://ubuntuforums.org/showthread.php?t=1082112&highlight=install+.tar.gz+files)

---

### Post by doublewitt on 2009-03-08
Here's a list I found for note-taking applications.
[http://linuxappfinder.com/utilities/notes](http://linuxappfinder.com/utilities/notes)

---

### Post by doublewitt on 2009-03-08
If anyone likes the GTD principle for note taking, then ThinkingRock might be what you are looking for.

**Web page:** 
[http://linuxappfinder.com/package/thinkingrock](http://linuxappfinder.com/package/thinkingrock)

Installation instructions:
    *  In "Applications" menu click on "Accessories" and then on "Terminal" item
    * Enter these commands:
      sudo -s
      echo deb [http://ppa.launchpad.net/salutis/ubuntu](http://ppa.launchpad.net/salutis/ubuntu) intrepid main > /etc/apt/sources.list.d/salutis.list
      aptitude update && aptitude install thinkingrock
    * In "Applications" menu click on "Office" and then on "ThinkingRock"

This is a nice and useful concept...

---

### Post by SergioJP on 2010-04-21
I am used notecase for a few years and now i use the new note taking sofware called **Cherrytree**.
features :

- rich text (foreground color, background color, bold, italic, underline, strikethrough, small, h1 and h2)
- syntax highlighting (only when the rich text is disabled in the current node)
- images handling: insertion in the text, edit (resize/rotate), save as png file
- lists handling (bulleted and numbered and switch between them, multiline with shift+enter)
- simple tables handling (cells with plain text)
- alignment of text, images and tables (left/center/right)
- hyperlinks (links to webpages, links to nodes/nodes + anchors, links to files)
- node print & node save as pdf file: support for rich text and code; images and tables are not considered in the printing yet, the paragraph justification is also not supported yet
- find a node, find in current node, find in all nodes
- replace in node names, replace in current node, replace in all nodes
- iteration of the latest find, iteration of the latest replace, iteration of the latest applied text formatting
- import from a notecase file, import from a cherrytree file

You can get in a *deb file here [http://open.vitaminap.it/software/cherrytree_0.9.5-1_all.deb]("ttp://open.vitaminap.it/software/cherrytree_0.9.5-1_all.deb")

And the program site is  [http://open.vitaminap.it/en/cherrytree.htm.](http://open.vitaminap.it/en/cherrytree.htm.)

---


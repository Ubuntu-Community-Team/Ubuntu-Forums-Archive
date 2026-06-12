---
title: "Ubuntu Software For University/College Student"
date: 2008-10-19
forum: Education &amp; Science
---

### Post by davidw89 on 2008-10-19
Hey guys i am a first year at Uni and i am trying to make the best out of using a laptop either during lectures or during my spare time (which i use to gather information).

I need a couple of programs that will hopefully make note taking/gathering a lot easier and need your help to recommend me on.

Firstly i need a Note taking apps that allows me to take note easily. I am using Tomboy at the moment but the program is not sophisticated enough.

Secondly i need a program for note taking Mathematical equations during my math class. The only program i know that could do this is OpenOffice Math but how do you install it/run it?

And lastly whenever i am on the internet i visit a lot of educational sites such has wikipedia/my university and i find really good information. Is there a way to index these notes for offline use? Normally i just add them to my bookmark or copy them to open office but that's a hassle..what's a good one that will work well with firefox.

Also where can i find a list of educational program available for Linux/Ubuntu?

I am also taking Physics so any programs suitable for that would be cool.

---

### Post by ilrudie on 2008-10-20
As far as making notes I use [tiddlywiki]("http://www.tiddlywiki.com/").  Its a self contained wiki and it works pretty good.  Not sure it will be fast enough or advanced enough for taking notes in class.  OO.o writer is probably the best choice (I used MS Office for mac when I was in school).  As far as equations in OO.o writer goto insert->object->formula to make nice looking equations.  I find this too slow for in class note taking.  Best to use good old paper/pencil for any serious math notes.

As far as getting websites for offline use I made a script that grabs whole sites.  It could be easily modified to grab only 1 page if thats what you wanted to do.  It grabs any pictures that are required and converts any links so they will work when downloaded (if you get mulitple pages that interlink the links will take you to the downloaded page not the actual website).  Its in the early stages of development and I still have more things I want to add but I can post the code if you'd be interested.  It uses wget from the terminal so if you are 100% opposed to terminal use its probably not for you.  Let me know if you are interested.

Add/Remove programs has an Education section where you can look at all the education tagged applications available in your repos.  Edubuntu is the educational flavor so you might get more education applications to look through if you add edubuntu repos to your apt sources.

I'm not really aware of any Physics programs so I can't help there.

---

### Post by Farmer of Bricks on 2008-12-22
If you're using KDE4, you could try Step and KMplot for physics and graphing, but they're not really note-taking application

---

### Post by giantoz on 2008-12-22
Flock web browser has this thing called webclipboard that would be perfect for indexing information from the net.  heres an article all about it.

[http://www.makeuseof.com/tag/flock-the-ultimate-student-browser/](http://www.makeuseof.com/tag/flock-the-ultimate-student-browser/)

gnomefiles has a good list of educational apps

[http://www.gnomefiles.org/category.php?cat_id=6](http://www.gnomefiles.org/category.php?cat_id=6)

freshmeat.net probably has a good list too.

also, basKet notes is a KDE app that is arguably the best note-taking app

[http://basket.kde.org/](http://basket.kde.org/)

---

### Post by samden on 2008-12-23
The best mathematical equations are created using LaTeX. You are just typing in text code to create your equations. The advantage is that they look great, and if you had all the code memorised you could take quick notes in class. The disadvantage is that you would have a lot of memorising to do before you could actually use it for notes!

I'd stick with a pen and paper for noting down equations, but learn LaTeX for actually typing stuff up.

I'd start moving away from word processors if I were you, using OpenOffice.org for taking notes is a massive overkill, it is a big slow program when all you really need is a snazzy text editor. I started writing my thesis in LaTeX 18 months ago and now I find I type nearly everything in plain text or LaTeX because it is quicker, simpler and more reliable than using a word processor. I really only open openoffice when I have to deal with a spreadsheet or someone emails me a .doc file.

Can't help you with the notetaking, I just know tomboy. But I'm sure there is something out there.

One day you'll have to deal with stats - keep R in the back of your mind for that, you may not need it yet.

---

### Post by ugm6hr on 2008-12-23
Zotero is good for documenting sites in FF: [http://www.zotero.org/](http://www.zotero.org/)

I would second Tiddlywiki as an easy way to save linked notes: [http://www.tiddlywiki.com/](http://www.tiddlywiki.com/)

---

### Post by christhemonkey on 2008-12-23
1. I just note take in gedit, never saw the need personally for anything else.

2. OOMath should be relatively painless to install (although I thought it was installed by default?)

3. Could you not just save a page off the internet (File -> Save) in firefox and then be able to access it at any time?

---

### Post by samden on 2008-12-23
+1 for Zotero. Well worth checking out. It is a reference manager that will not only record stuff of the net and be a database of references, but will insert references into OpenOffice (or Word) as well, just like Endnote.

---

### Post by euler_fan on 2008-12-24
> **samden said:**
> The best mathematical equations are created using LaTeX. You are just typing in text code to create your equations. The advantage is that they look great, and if you had all the code memorised you could take quick notes in class. The disadvantage is that you would have a lot of memorising to do before you could actually use it for notes!

I'd stick with a pen and paper for noting down equations, but learn LaTeX for actually typing stuff up.

I'd start moving away from word processors if I were you, using OpenOffice.org for taking notes is a massive overkill, it is a big slow program when all you really need is a snazzy text editor. I started writing my thesis in LaTeX 18 months ago and now I find I type nearly everything in plain text or LaTeX because it is quicker, simpler and more reliable than using a word processor. I really only open openoffice when I have to deal with a spreadsheet or someone emails me a .doc file.

Can't help you with the notetaking, I just know tomboy. But I'm sure there is something out there.

One day you'll have to deal with stats - keep R in the back of your mind for that, you may not need it yet.

I largely concur with this post. LaTeX is the best way to take computerized notes in a scientific or mathematical class, the problem is that you can't get diagrams into it very quickly, nor copy down tables or any number of other things and still have the code be halfway readable. Paper and pencil are best in this context.

However, I have some very pretty theology notes I did in LaTeX once upon a time . . . TeXMaker is a nice LaTeX editor.

R is amazing. Taking the time to learn it is well worth it. However, you're best off learning Emacs at the same time in order to leverage ESS.

---


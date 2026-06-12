---
title: "Is there any advanced WYSIWYG editor for Ubuntu"
date: 2009-06-15
forum: General Help
---

### Post by ongun.kanat on 2009-06-15
I'm searching a WYSIWYG editor for ubuntu.It must have a internal php editor like Dreamweaver.It can be a eclipse or aptana studio plugin.

---

### Post by Dragonbite on 2009-06-15
the first WYSIWYG editor that comes to mind is Kompozer. I don't know of any Eclipse or Aptana plug-ins.

I also like [[COLOR="Blue"]Quanta Plus[/COLOR]]("http://quanta.kdewebdev.org/"), which isn't fully "WYSIWYG", but it does show the layout and tags for behind code. One feature I like is the split screen where you can see the code on the bottom and the layout on the top pane and changes made to one is quickly updated in the other.

You can see what I'm talking about with this [[COLOR="Blue"]screenshot[/COLOR]]("http://quanta.kdewebdev.org/viewscreenshot.php?id=4&application=quanta").

---

### Post by ongun.kanat on 2009-06-15
I know Kompozer and Quanta+ but they are only html desingers.But I'd like to design php pages.They cannot edit php.

So, I want a ide which has wysiwyg designer and php code support.

E.G
[IMG]http://theopensourcery.com/images/phpdreamcs4.gif[/IMG]

When I'm using WinXp, I've installed Adobe DW.Now I'm using Ubuntu but I can't  find any designer like DW

---

### Post by Dragonbite on 2009-06-15
> **ongun.kanat said:**
> I know Kompozer and Quanta+ but they are only html desingers.But I'd like to design php pages.They cannot edit php.

So, I want a ide which has wysiwyg designer and php code support.

When I'm using WinXp, I've installed Adobe DW.Now I'm using Ubuntu but I can't  find any designer like DW

I guess I don't understand the edit PHP. I thought Quanta included some PHP tools.

I know it's unrelated, but I think there is a PHP plug-in for Netbeans. Kinda heavy for just one aspect, but may meet  your requirements.

Of course, another question is whether DW works in WINE or not?  It's not idea but may (barely) fit the bill.

---

### Post by ongun.kanat on 2009-06-15
I used netbeans.It has not wysiwyg design function.I'm using Netb. to develop Java Apps.

Is there some plugins for Quanta to edit php?

---

### Post by thfz on 2009-06-15
I believe that you should experiment more thoroughly with Kompozer. I just messed around with it a bit and it seems perfectly capable of letting you code in PHP. Just click the "Source" tab at the bottom of the editor window to look at the HTML and put the PHP that you want in there, then save the file as a .php

---

### Post by nlinecomputers on 2009-06-15
You are not going to find one.  Such a thing is not possible.

PHP is a programing language.  HTML a rendering language.  Your program would have to have it's own built in PHP server.  Besides most PHP code is modules that by themselves can't do much. Or they do things that aren't visually related like changing variables or calling or storing data in a SQL table.  They are called by the main script as needed.   The only way to do what you want is by loading a PHP/Apache server and using your browser to view the results, which probably would not be the code you are working on.

---

### Post by Mirge on 2009-06-15
> **nlinecomputers said:**
> You are not going to find one.  Such a thing is not possible.

PHP is a programing language.  HTML a rendering language.  Your program would have to have it's own built in PHP server.  Besides most PHP code is modules that by themselves can't do much. Or they do things that aren't visually related like changing variables or calling or storing data in a SQL table.  They are called by the main script as needed.   The only way to do what you want is by loading a PHP/Apache server and using your browser to view the results, which probably would not be the code you are working on.

I would say you're way off base here saying such a thing is not possible.

Takes 5-10 mins to install apache, php and mysql if he DID want to set up his own webserver in Ubuntu.

Some versions of dreamweaver actually work fine in Ubuntu, check [http://appdb.winehq.org/](http://appdb.winehq.org/). Also, you might consider just installing VirtualBox and throwing windows on it if you really must have a good WYSIWYG editor. I haven't run into one either. I run Expression Web in a virtualbox.

---

### Post by nlinecomputers on 2009-06-15
I think you misunderstand.  Plenty of programs can display and recognize PHP code.  I don't know any that will actually run it from within the program.  Because it isn't a markup language it is programing language.

That is like saying visual studio will constantly run your Visual Basic programs on the fly.  Doesn't happen that way.

---

### Post by Mirge on 2009-06-15
> **nlinecomputers said:**
> I think you misunderstand.  Plenty of programs can display and recognize PHP code.  I don't know any that will actually run it from within the program.  Because it isn't a markup language it is programing language.

That is like saying visual studio will constantly run your Visual Basic programs on the fly.  Doesn't happen that way.

Where did you read that the editor itself must run the program from within itself? MANY ide's will run a php script, given you have (for example) php5-cli installed. I use Geany, it does just that... click "Compile" and it runs php lint against the script. Either I completely overlooked where he said he wants an IDE that includes php within it and the ability to run programs in it...... or you are mistaken. If you did want to run a PHP script within an IDE, all you'd have to do is include a browser within the IDE. Like I mentioned, you'd need apache, php and (optionally) mysql installed.

Also, Visual Basic is a compiled language, PHP is an interpreted language. So the comparison really isn't valid at all.

---

### Post by nlinecomputers on 2009-06-15
Well perhaps I misunderstand what he wants but he said he wanted to WYSIWYG edit PHP files.  I can't see how one can do that.  Never seen Geany I'll have to look at it.

---

### Post by Dragonbite on 2009-06-15
> **ongun.kanat said:**
> I used netbeans.It has not wysiwyg design function.I'm using Netb. to develop Java Apps.

Is there some plugins for Quanta to edit php?

I looked quickly at [[COLOR="Blue"]Quanta's documents[/COLOR]]("http://quanta.kdewebdev.org/docs.php") and they have a list of tutorials which make it sound like it has the PHP and debugging capabilities.

> [_Quanta as a Docbook Editor_]("http://quanta.kdewebdev.org/tutorials/quanta-docbook/quanta.html")
An article written by Carlos Leonhard Woelz about how Quanta can be used to write docbook documents.

[_Quanta and Gubed_]("http://www.hoernerfranzracing.de/kde/gubed.html")
Tutorial about how to set up Quanta and Gubed to debug PHP documents written by Werner Joss.

[_PHP debugging with Gubed_]("http://www.very-clever.com/quanta-gubed-debugging.php")
Another tutorial about how to set up Quanta and Gubed to debug PHP documents written by Ewald Kicker. German and Dutch versions are also available.

[_PHP debugging with XDebug_]("http://blog.koehntopp.de/archives/1978-PHP-5-Debuggen-mit-Xdebug-und-vim-oder-Quanta.html")
A German language page describing how to use XDebug with Quanta, written by Kristian Köhntopp.


Hope that helps. Otherwise I may not be understanding what you mean by PHP editing.  Ultimately, since it is a scripting language you can use GEdit even, and I think that includes PHP syntax coloring without the WYSIWYG aspect.  That's what I have in my mind as "PHP editing".

---

### Post by ongun.kanat on 2009-06-15
Thanks for all.But I've installed new version of quanta+ found some plugins for quanta at this page [http://quanta.kdewebdev.org/resources.php]("http://quanta.kdewebdev.org/resources.php")
But I can't install them.How can I install them.
E.G->[http://209.208.122.238/kdewebdev/newstuff/quanta/toolbar/php.toolbar.tgz]("http://209.208.122.238/kdewebdev/newstuff/quanta/toolbar/php.toolbar.tgz")

---

### Post by Mirge on 2009-06-15
Why can't you install them?

---

### Post by ongun.kanat on 2009-06-15
> **Mirge said:**
> Why can't you install them?
Because I don't understand how to do it.

---

### Post by Mirge on 2009-06-15
> **ongun.kanat said:**
> Because I don't understand how to do it.

I mean did you try & ran into specific errors?

---

### Post by Dragonbite on 2009-06-15
They look like .tar.gz's so if you open them up (double-click to open the archiver) there may be an INSTALL.txt type file to step into how to add them.

---

### Post by Francewhoa on 2009-06-23
KompoZer 0.7.10 is unstable with Ubuntu. Try the latest version 0.8 alpha it's more stable. The new version has views/tabs built in and spit window like Dreamweaver. Find this post: [http://ubuntuforums.org/showpost.php?p=7501868&postcount=6](http://ubuntuforums.org/showpost.php?p=7501868&postcount=6)

---


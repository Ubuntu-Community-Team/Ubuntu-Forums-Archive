---
title: "Texmaker freeze on Jauntu"
date: 2009-05-06
forum: General Help
---

### Post by dox_drum on 2009-05-06
Hi everybody!

I'm a grad. student on Physics. For this reason I write a lot using LaTeX. I get used to Kile, but the new environment is not so grateful as the one of the former version... so I move toward TexMaker.

However, the latter sort of freeze from time to time... fortunately one still can save the changes before closing the program. But the cursor desappears and the keyboard works no more.

Has anyone note the problem? or better than that... Had someone solved it?

Thank you very much!

P.D.:
[LIST]
[*]Distro: Jaunty (32-bits)
[*]Currrently using Emacs
[*]If someone knows how to downgrade the kile to the former version, I'd thank some directions
[/LIST]

[CENTER]Enjoy![/CENTER]

---

### Post by lethalfang on 2009-05-08
I gave up trying to get the new kile to work in Jaunty, and installed the older version and it works just fine (as well as it did before). 
[https://launchpad.net/ubuntu/+source/kile](https://launchpad.net/ubuntu/+source/kile)
Install the intrepid one. 

And for me, kile isn't complete without kdvi:
[http://packages.ubuntu.com/intrepid/kdvi](http://packages.ubuntu.com/intrepid/kdvi)

---

### Post by entropy1 on 2009-05-17
I have been using texmaker for a while.  Since I upgraded to Jaunty, I noticed that sometimes after I use "find" to search for text, the cursor no longer appears, and I cannot edit text in that tab.  I can save it, close it with ctrl-w, reopen it, and the cursor comes back.  However, this is too annoying!

I tried reinstalling, uninstalling, reinstalling.  I tried changing visual effects.  Nothing helped.

I gave up and completely removed texmaker.  Now I use Kile 2.1, which I run under gnome.

---

### Post by XCan on 2009-05-17
After having tried all the 'standard' so called latex editors, I found them all to be bloated and slow (much like programs for Windows) for no apparent reason. Thus, I can **strongly** recommend to latex plugin for gedit [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin) . Lightweight, easy to configure and very fast! It can be found in the package manager under the name "gedit-latex-plugin".

---

### Post by dox_drum on 2009-05-17
You are right, after trying almost everything I got back to kile. Even I solve some of the problems of its configuration... but still prefer the previous version.

Thank you both.

---

### Post by dox_drum on 2009-05-17
> **XCan said:**
> After having tried all the 'standard' so called latex editors, I found them all to be bloated and slow (much like programs for Windows) for no apparent reason. Thus, I can **strongly** recommend to latex plugin for gedit [http://live.gnome.org/Gedit/LaTeXPlugin](http://live.gnome.org/Gedit/LaTeXPlugin) . Lightweight, easy to configure and very fast! It can be found in the package manager under the name "gedit-latex-plugin".

Thank you very much for the wonderful suggestion. 4sure I'll try it!


It works like a charm!!

---

### Post by XCan on 2009-05-17
Glad I could help! :)

---

### Post by entropy1 on 2009-07-11
A solution that worked for me is to use a more recent version of Texmaker than is available in the repos.:

1) Uninstall repository-version of Texmaker using synaptic.
2) Download latest appropriate .deb version of Texmaker from

[http://www.xm1math.net/texmaker/download.html#linux](http://www.xm1math.net/texmaker/download.html#linux)

3) After you download the appropriate .deb file, right click and select Open with "GDebi Package Installer".

4) Enjoy the latest version of Texmaker.

---

### Post by gbajra on 2009-07-13
I am newbie in linux. I used texnicceter in windows and I appreciated the software after I tried linux ones. I thought linux would be more latex friendly and would have user friendlier softwares.

After few search led to kile. Tried that, it is not at all user friendly. I started with a correct file and made a deliberate mistake in the tex file and try to get to the mistake. The output is garbage.

Then tried emacs as many were trying. Too many shortcuts, what is it for? I was trying to do something in emacs and using Control key plus something and it started capitalizing the words.

Then texmaker, was very pleased to see the texniccenter layout. Gives comprehensive error message with line number and line number is in the editor also. Was quite happy until I discovered the keyboard freezes for the program. Could not type. Oh what the hell, uninstalling linux and moving back to good old windows with texniccenter and miktex.

---

### Post by guayca on 2009-10-02
Hi everyone,

I also experienced the freezing and the disparition of the cursor in TexMaker, but I found a solution. When the keyboard won't work, simply click on the chapter you are editing under the Structure bar. Your cursor re-appears at the beginning of the chapter. 

Hope it works for you!

ps: I'm also on Jaunty 32 bits.

---

### Post by jeneverboy on 2010-08-18
Hi,

Closing and re-opening document will also work against freezing. But it is not a real solution ofcourse :(.

Texmaker and linux are faster then anything in windows.

Bye

---


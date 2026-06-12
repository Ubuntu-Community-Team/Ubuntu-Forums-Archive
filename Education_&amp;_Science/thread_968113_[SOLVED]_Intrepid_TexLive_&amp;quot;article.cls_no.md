---
title: "[SOLVED] Intrepid TexLive &amp;quot;article.cls not found&amp;quot;"
date: 2008-11-02
forum: Education &amp; Science
---

### Post by CalderCoalson on 2008-11-02
Ok, so I installed a Intrepid yesterday, and installed TexLive via apt-get, but now when I try to compile a .tex file, it fails saying "LaTeX Error: File `article.cls' not found."  I did a search for article.cls, and sure enough there isn't anything with that name on my computer.

I have no idea what's going on and I have math homework due on Tuesday.  Please please please help.

Thanks,
-Calder Coalson

---

### Post by WW on 2008-11-02
I don't recall the standard suite of packages one should install to get a complete Latex installation, but a little poking around at packages.ubuntu.com shows that the package [texlive-latex-base](http://packages.ubuntu.com/intrepid/texlive-latex-base) has the file /usr/share/texmf-texlive/tex/latex/base/article.cls

---

### Post by CalderCoalson on 2008-11-02
Thanks so much for the reply, but unfortunately it doesn't really solve anything: I have texlive-latex-base installed.  Should I uninstall and reinstall?  Also, could it have something to do with updmap-sys, whatever that is?  I don't remember seeing that every time I had to install or remove a latex package under Hardy, but it shows up whenever I do now.

---

### Post by CalderCoalson on 2008-11-02
When computers act illogically, it makes me feel stupid, because I know it has perfectly good reasons for doing what it's doing, but I just don't understand them.  I uninstalled and reinstalled and now there is a article.cls file in /usr/share/texmf-texlive/tex/latex/base, but I get the error "File `amsfonts.sty' not found."

---

### Post by CalderCoalson on 2008-11-02
That was really weird.  I eventually just did:
```

sudo apt-get purge texlive
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get install texlive

```
and now it works.  Something must have gotten corrupted or deleted or who-knows-what.  1 problem down, 3 to go: [http://ubuntuforums.org/showthread.php?p=6089631#post6089631](http://ubuntuforums.org/showthread.php?p=6089631#post6089631) *sigh*

---

### Post by Randy Schilling on 2012-06-29
Here is I think possibly a better solution.  
I suspect your system contained the article.cls file right from the beginning.
Your system could not find the file because you didn't specify the TEXINPUTS variable.

I ran into the error message months ago when I was trying to setup the Kile editor.
I added the following directory to my TEXINPUTS environment variable:

/usr/local/texlive/2011/texmf-dist/tex/latex/base

I guess that directory might be different on your system but on my  system this is the directory containing article.cls (even though tex  and  latex report that they can't find that file).
 

If your running Kile this is done in Kile's configuration routine.

I'm not satisfied with Kile so today I tried adding the LateX plugin to gedit.
After setting up the plugin, I latexxed a file and the system could not
find article.cls.  I forgot how I solved the problem previously to I googled
the error message.  That's how I found your thread.

Then I remembered my old solution and I learned the following.
The system apparently can't see Kile's TEXINPUTS and,
for some reason, Kile can't see the system's TEXINPUTS variable either.
I had to setup TEXINPUTS twice.

If you want to tex or latex from a bash terminal or from gedit with the latex 
plugin, you have to set TEXINPUTS  in your ~/.profile file.  

If you need more info on setting up variables let me know.  You might have to reboot
or say something like source~/.profile at your bash prompt.

Now I got two editors running but I'm not satisfied with either one of them, Kile
or gedit with the LaTeX plugin.  The problem with gedit is that the plugin supports
latex only and does not support tex. 

good luck and regards - Randy

---

### Post by overdrank on 2012-06-29
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


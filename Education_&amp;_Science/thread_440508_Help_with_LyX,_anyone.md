---
title: "Help with LyX, anyone?"
date: 2007-05-11
forum: Education &amp; Science
---

### Post by elfstone214 on 2007-05-11
I compiled and installed LyX 1.5.0 beta2 and I am trying to add a class for my thesis (gatech-thesis.cls)
([http://www.grad.gatech.edu/thesis/gatech-thesis-1.7.tar.gz](http://www.grad.gatech.edu/thesis/gatech-thesis-1.7.tar.gz))

I have followed these installation instructions:
> The following files should end up in your texmf tree
(or your localtexmf tree) at these locations:

   <texmf>/tex/latex/gatech-thesis/gatech-thesis.cls
   <texmf>/tex/latex/gatech-thesis/gatech-thesis-patch.sty
   <texmf>/tex/latex/gatech-thesis/gatech-thesis-losa.sty
   <texmf>/tex/latex/gatech-thesis/gatech-thesis-gloss.sty
   <texmf>/tex/latex/gatech-thesis/gatech-thesis-index.sty
   <texmf>/bibtex/bst/gatech-thesis/gatech-thesis.bst
   <texmf>/bibtex/bst/gatech-thesis/gatech-thesis-losa.bst
   <texmf>/makeindex/gatech-thesis/gatech-thesis-index.ist

Then, you need to update the file database; usually this is
something like "initexmf -u".  On MikTeX, you run the "MikTeX
Options" program, and on the "General" tab, in the "File name
database" section, click on the button that says "Refresh Now".


however I do not have a ""initexmf" command, I simply did "texhash" but I dunno if this updating the file database. Then I "reconfigured" within LyX, exited, and restarted. But I still cannot see the class withing LyX.

Is anyone familiar on how to do this?

---

### Post by kleeman on 2007-05-11
Try these instructions:

[http://telin.ugent.be/~slippens/drupal/customLaTeXclassesinLyX](http://telin.ugent.be/~slippens/drupal/customLaTeXclassesinLyX)

---

### Post by elfstone214 on 2007-05-11
I don't understand .... I followed these new instructions and the class and other files are all updated within Ls-R, yet when I reconfigure and restart, it still does not show up under document class.

---

### Post by Typhoon on 2007-05-12
LyX itself contains information on installing a new class: see Help -> Customization section 5.1.

That section says to finish up by reconfiguring LyX through the Tools -> Reconfigure menu, then restarting LyX.

My version of LyX is 1.4.3, so the details may vary slightly if you are using a more recent version.

LyX is a great package - I used it to publish a cookbook that my wife wrote. some sample pages here: [http://web.aanet.com.au/sage](http://web.aanet.com.au/sage).

HTH,
Typhoon

---

### Post by Typhoon on 2007-05-12
Sorry - I didn't read your first post carefully enough. I see that you did Reconfigure.

Typhoon

---

### Post by elfstone214 on 2007-05-12
> **Typhoon said:**
> 
My version of LyX is 1.4.3, so the details may vary slightly if you are using a more recent version.


I have been able to install the class in Lyx 1.4.x, but unfortunately I began writing my thesis in Lyx 1.5.0 beta (windows XP) and I cannot open it with the older 1.4 version. So now I am stuck trying to get 1.5.0 working here in Linux.

---

### Post by Typhoon on 2007-05-12
Do you still have access to the Windows machine? If so, you could export as LaTeX, then import that into your 1.4.x version.

Typhoon

---

### Post by elfstone214 on 2007-05-12
> **Typhoon said:**
> Do you still have access to the Windows machine? If so, you could export as LaTeX, then import that into your 1.4.x version.

Typhoon

hmmm didn't think of that (I am still a lyx noobie)... I will go check it out and report back :)

---

### Post by kleeman on 2007-05-12
There is an option in my lyx 1.5 beta2 on linux to export the file to lyx 1.4 format (File---> Export)

Sounds as if you may have hit a bug in 1.5 since I checked the docs and the procedure for installing the new class has not changed. You might want to ask on the lyx user list. You can subscribe to the list at 

gmane.editors.lyx.general

I subscribe to this newsgroup from within thunderbird.

---

### Post by elfstone214 on 2007-05-12
I uninstalled 1.5.0 and reinstalled 1.4.3, but once again I cannot replicate what I did before to get the class in there. So I ended up reinstalling 1.5.0 because I realized I have figure floats which I believe are only a 1.5.0+ feature.

So to summarize I am back where I started. I will keep researching this and if I find the solution I will report back. If anyone else has any other recommendation, please shoot it this way!

---

### Post by kleeman on 2007-05-12
1.4.3 does actually support Figure floats. I use it all the time. Might be worth having a good read of the users manual which is accessible from the menu (Notice how politely I didn't say RTFM :lolflag: )

---

### Post by elfstone214 on 2007-05-12
> **kleeman said:**
> 1.4.3 does actually support Figure floats. I use it all the time. Might be worth having a good read of the users manual which is accessible from the menu (Notice how politely I didn't say RTFM :lolflag: )

either way I still cannot install the class in either one right now ](*,)

I am positive that it is not Lyx anyway. I can open my thesis.lyx but I cannot build it because it is missing the class ... it has to be a latex related issue. I have two folders for "texmf", one is simply /usr/share/texmfm and the other is /usr/share/texmf-tetex

when I run texhash now it updates /var/libs/ls-R and when I open it my class folder is not in there. I don't understand in which folder it is looking in. This is driving me "INSANE" to put it mildly.

---

### Post by kleeman on 2007-05-12
If you export it to latex does it compile then using the latex command? i.e. does a latex file using your class work? If not then something has gone wrong in your latex installation of the class files.

---

### Post by parktownprawn on 2007-05-13
Try putting the packages in  ```
/usr/local/share/texmf/

```

What is the output of  ```
sudo texhash
```

What happens if you just try running latex on your thesis (in tex format) ?

---

### Post by elfstone214 on 2007-05-13
I don't have a /usr/local/share/texmf/ folder but I do have /usr/share/texmf/

I put them there and "texhash", reconfigured, and nothing. I think texhash is not looking in the right locations. I have tried adding other classes without success either. I did add the "beamer-class" using sudo apt-get install beamer-class, and that worked beautifully.

I exported it as latex (plain) and ran "latex thesis.tex", it ran although there were some errors and it still produced a dvi file which I opened. The dvi file looks ok but missing a lot of the formatting (which I need) and figures do not show up.

---

### Post by kleeman on 2007-05-13
Try this (and give us the output at each stage!!!):

sudo mkdir /usr/local/share/texmf/

sudo cp ****.tar.gz /usr/local/share/texmf/


(where ****.tar.gz is the name of your package of style files)

sudo su
cd /usr/local/share/texmf/
tar zxvf ****.tar.gz 
texhash

---

### Post by elfstone214 on 2007-05-13
kleeman, I did your steps and everything went smooth (no errors)

opened lyx, reconfigure, closed, reopened lyx, and it still does not show up. When I open my thesis.lyx it says the gatech-thesis class is unknown, then it opens the file and gives another error message about the gatech-thesis.layout being unknown too.

Later on, I am going to try and see if I can replicate what the "beamer-class" did and where it installed itself and see if that works with my class.

---

### Post by kleeman on 2007-05-13
Did you create a layout file for lyx and put it in $HOME/.lyx/layouts   ???
See my howto in post #2 at the top of the thread for specific instructions.
Lyx needs that layout file to see the class.

They give you a sample file with the lines

#% Do not delete the line below; configure depends on this
#  \DeclareLaTeXClass[funkyarticle]{article (funky)}
 
# Input general definitions
Input stdclass.inc
 
you need to change funkyarticle to gatech-thesis here
and funky to gatech

Hopefully the after reconfiguring lyx will see the gatech class.

---

### Post by elfstone214 on 2007-05-13
kleeman that did it!  I had put the layout in the wrong folder. But it is now all working!!

Thanks a lot man and to everyone who helped! I am now fully up and running on Linux :guitar:

---

### Post by kleeman on 2007-05-14
No worries. Good luck with your thesis!

---


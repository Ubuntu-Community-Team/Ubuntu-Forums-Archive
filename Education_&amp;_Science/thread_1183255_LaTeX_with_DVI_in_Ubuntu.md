---
title: "LaTeX with DVI in Ubuntu"
date: 2009-06-09
forum: Education &amp; Science
---

### Post by inac on 2009-06-09
Hi, has anyone successfully installed LaTeX with DVI and preview on Ubuntu? Please post results here. Thanks!

---

### Post by bryncoles on 2009-06-10
yes - just install all the texlive packages form the repos. particularly the base package. 

is there something specific you're having issues with (not that i can help - im just trying to learn latex now...)

*edit* you've only 4 beans... do you know about the repo's? you might need the multiverse repo enabling...

you can do that by following the advice [here]("https://help.ubuntu.com/community/Medibuntu#Adding the Repositories"), then fire up synaptic package manager and type 'latex' into the search box. install all the texlive packages (i would). 

then, to use latex, open your favourite word processing document, type away in the usual way and save whatever in the usual way for latex - whats that, as a .tex file? then open a terminal (applications, accessories, terminal). use the 'cd' command to move to where your latex document is saved thusly:

```
cd ~/Desktop/latex_file
```

here, ive assumed you have created a folder on your desktop, and called the folder 'latex_file'. 

then type into the terminal 

```
latex filename
``` to run it through the dvi hoops. or type
```
pdflatex filename
``` to create a pdf. 

quite straight forward, once you know what you're supposed to be doing!

---

### Post by lethalfang on 2009-06-10
> **inac said:**
> Hi, has anyone successfully installed LaTeX with DVI and preview on Ubuntu? Please post results here. Thanks!

I use Kile and KDVI from the Intrepid repo (because the Jaunty repo has gotten rid of KDVI and the new Kile is very unstable). 

[https://launchpad.net/ubuntu/+source/kile](https://launchpad.net/ubuntu/+source/kile)
[https://launchpad.net/ubuntu/intrepid/+source/kdvi/4:3.5.10-0ubuntu1](https://launchpad.net/ubuntu/intrepid/+source/kdvi/4:3.5.10-0ubuntu1)

---

### Post by spinoza666 on 2009-06-14
> **inac said:**
> Hi, has anyone successfully installed LaTeX with DVI and preview on Ubuntu? Please post results here. Thanks!

Yes. As previously stated, just install texlive through synaptic or apt-get, and pick an editor of your liking. This will give you preview by dvi. Editors that give you this functionality would for example be kile for kubuntu or texmaker if you are running vanilla ubuntu. I would also recommend emacs with the auctex package for added efficiency. If you are new to latex, texmaker or kile would probably be the best place to start, while emacs is an excellent option if you are a bit more latex savy, and don't mind reading up a bit before you start.

---


---
title: "'Lost' TeXLive after reboot..."
date: 2006-02-04
forum: Desktop Environments
---

### Post by dada1958 on 2006-02-04
Hi, I'm a Mac man, discovering Linux Ubuntu on a second PC. Ubuntu 5.10 is still having teTeX 2 in its repositories, not that recent... Yesterday I read in the comp.text.tex newsgroup about [TeXLive](http://www.tug.org/texlive/) and I decided to take the risk, removed teTeX from my Ubuntu PC and downloaded and burned the TeXLive 2005 ISO.
I'm still not an Unix hero yet but thanks to the online documentation I managed to get through the initial (full) installation.
After pasting a 'PATH=/usr/local/texlive/2005/bin/i386-linux:$PATH; export PATH' in terminal things seemed to work. Great! I was delighted, even more when things like hanging punctuation and margin kerning finally worked on my Ubuntu PC.
For some stupid reason I thought I had to reboot. I shouldn't have done that but I did and when I wanted to continue my playing around with TeXLive, pdflatex in particular, I got the dreadful message in terminal: command not found. Rereading the online documentation learned me that I was probably too impatience again, I didn't put 'PATH=/usr/local/texlive/2005/bin/i386-linux:$PATH; export PATH' in the $HOME/.profile file. So I did that later.
> # ~/.profile: executed by Bourne-compatible login shells.

if [ "$BASH" ]; then
    if [ -f ~/.bashrc ]; then
	. ~/.bashrc
    fi
fi

mesg n

PATH=/usr/local/texlive/2005/bin/i386-linux:$PATH; export PATH



That didn't work:

niels@p3:~$ latex --version
bash: latex: command not found
niels@p3:~$

TeXLive runs after entering 'PATH=/usr/local/texlive/2005/bin/i386-linux:$PATH; export PATH' in terminal.

So my question is: what am I doing wrong and what do I have to do to get TeXLive running?
TIA

---

### Post by dada1958 on 2006-02-05
I was suggested to put the path in /etc/bash.bashrc and that worked :D

---


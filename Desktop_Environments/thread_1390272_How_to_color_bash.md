---
title: "How to color bash?"
date: 2010-01-25
forum: Desktop Environments
---

### Post by surfinmdq on 2010-01-25
Hi,

lately I've been playing with latest Sabayon 5.1 and while there were some things I like I still are (and will be) a Debian/Ubuntu fan.

One of the things I liked very much from Sabayon was the colorful bash and the way different files and folders are colored when 'ls' is issued; also I remember Linux Mint has a cool bash too, colorful and with lot of qoutes everytime you open the terminal.

I would like to know if there's any guide here in the Ubuntu community to achieve same thing.

Thanks! :)

---

### Post by Lars Noodén on 2010-01-25
As far as I can tell, [ANSI Escape Sequences](http://tldp.org/HOWTO/Bash-Prompt-HOWTO/x329.html) are already used to set colors used for activities in bash.  

For example in default Karmic Koala, I see directories as blue, executable files as green when running ls in the shell via KDE's program, Konsole.  But that has nothing to do with console, only your settings in ~/.bashrc or ~/.bash_aliases

---

### Post by mcduck on 2010-01-25
actually ls output should be colored already, at least if you haven't messed with your aliases.

Colored command prompt itself can be enabled in ~/.bashrc. Read through the file and you'll find a line that tells you to uncomment it if you wish to enable colored prompt.

..and if you want a quote when you open a terminal, just install "fortunes", some fortune packages you like, and then add a command to run it into the end of the bashrc file.

---

### Post by dewcansam on 2010-03-14
reopen and bump

Well i know that colors are handled in the ".bashrc" config file. And i am already outputing in color. i need / want to change those colors. It has been so very long since i needed to do something like this. If i remember correctly in RedHat we used to set the shell var LS_COLORS. Is this still the same way to change them in Ubuntu ? Does anyone have any examples ?

---

### Post by dewcansam on 2010-03-14
since i never give up trying to find the answers to my own stuff. 

Check out this info
[http://www.bigsoft.co.uk/blog/index.php/2008/04/11/configuring-ls_colors](http://www.bigsoft.co.uk/blog/index.php/2008/04/11/configuring-ls_colors)

Ubuntu uses the command
```
eval "`dircolors -b`"
```
in the file "~/.bashrc" to set the colors for the standard shell

Add these lines to the bottom of your "~/.bashrc" to change the colors
```

### colors key 00=default 01=bold 04=underline 05=flash 07=reverse 08=concealed                                                                                     
### font 31=red 32=green 33=orange 34=blue 35=purple 36=cyan 37=grey 90=dk_grey 91=lt_red 92=lt_green 93=yellow 94=lt_blue 95=lt_purple 96=turqoise 97=white
### background 40=black 41=red 42=green 43=orange 44=blue 45=purple 46=cyan 47=grey 100=dk_grey 101=lt_red 102=lt_green 103=yellow 104=lt_blue 105=lt_purple 106=turquoise
LS_COLORS="no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35"
export LS_COLORS

```
then just change the the colors
from "ln=01;36:"
to something like "ln=01;36;47:"
this just changes the background color for sym links to grey

---


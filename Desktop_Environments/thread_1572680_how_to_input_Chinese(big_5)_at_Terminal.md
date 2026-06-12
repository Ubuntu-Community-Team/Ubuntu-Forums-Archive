---
title: "how to input Chinese(big 5) at Terminal"
date: 2010-09-11
forum: Desktop Environments
---

### Post by tanyeun on 2010-09-11
I can display Chinese using gnome terminal

I can input Chinese using VI thru gnome terminal

but I can not input Chinese(Big 5) correctly on the command line
I use scim/bridge as my input method

any help?

thx,

David

---

### Post by tanyeun on 2011-03-08
solution I found :
1. make sure you installed english and chinese packages 
in the "Language Support"> $ gnome-control-center

2. installed gcin or scim properly so that you can at least
input Chinese in the browser

3. Set the locale to Unicode( UTF-8 )
> $vi ~/.bashrc
and add
> 
export LANG="en_US.utf8"
export LC_ALL="en_US.utf8"
export LC_CTYPE="en_US.utf8"

> $source ~/.bashrc

Then I can both input Traditional Chinese or Simplified Chinese
in gnome-terminal, and my shell can understand Chinese and
display Chinese filenames as well

PS: if your current locale is set to ANSI something
your system must> export LC_ALL="C" somewhere
For example, I used to put this line in my startup file in fluxbox and it messed me up a lot before I found this problem.

---

### Post by Rodney9 on 2012-02-19
Go to Menu - Preferences - Language Support

It may ask you, it did for me, to install language support for other software, for me it was Thunderbird Libre Office etc.

You can install other languages and drag which language you want as default, plus set a language system wide.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---


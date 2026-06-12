---
title: "Interesting Xserver-Xorg solution to NVIDIA driver problems"
date: 2008-08-20
forum: Gaming &amp; Leisure
---

### Post by Hellion DarkLord on 2008-08-20
Hello PPL!

I have been experiencing problems with the NVIDIA-Linux-x86-173.14.09-pkg1.run in Kubuntu 8.04.  I was getting VERY frustrated because no matter what I did I was unalbe to run the Nvidia driver.  I read all the man pages for everything.

$man nvidia-xconfig
$man nvidia-settings
$man xserver-xorg

Anything I could find I read.  I started getting VERY dangerous with my system and executing dangerous commands in the persuit of gaming happiness.  I finally decided to do something that I think is may work for some of you. You MUST read all of the manual pages I have listed and anything else you can get your hands on before trying this.

I executed the command 
```
sudo nvidia-xconfig -T
```

This shows you everything that the xconfig will write to your xorg.conf file that determines the xserver layout of your machine WITHOUT writing it to the file.  Option -T tells the xconfig to simply print the output in the terminal.  Compare this printed output to the file in ect/X11/xorg.conf preferably before installing the driver. Even go so far as to make a copy of said output because you may want to compare it to later output from xconfig.

Next, open the text editor and copy all of the commands under the "advanced help" section in (#man nvidia-xconfig) to it.  only copy and paste the actual commands such as: 
```
--force-generate
``` 
(though you probably don't want to use that one!)  
once all of the commands have been copied use;
```
nvidia-xconfig -T [followed by all the --force-generate type commands in your text file]
```

be sure to leave spaces between the commands and retain all the --'s because otherwise it will exit with an error.  It will probably do so anyway, but that's okay, read the errors and omit the problematic commands.  

Once you have done that then compare the output with the original xorg.conf and find any differences.  Now you need to research these differences and make CERTAIN you understand them. (If there are any differences)

If differences are seen you MAY be able to have a better gaming experience, but playing with your xorg.conf is VERY dangerous!  You can break your entire system with a tiny little change.  Make certain you want to even make the changes because some of them may not even be something you want.

That said, have fun, but don't break your system.  

Happy gaming all!

---


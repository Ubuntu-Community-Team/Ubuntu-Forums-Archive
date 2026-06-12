---
title: "In Ubuntu 9.04, forward and inverse search between Kile 2.1 and Okular"
date: 2009-04-23
forum: General Help
---

### Post by lethalfang on 2009-04-23
How to do it?
It used to work with kile 2.0 and Kdvi in 8.10, but the 9.04 wiped out Kdvi, and I can't get Okular to work with Kile 2.1 in reverse/forward search. 

Kile 2.1 also seems to crash quite often. 

Thanks

---

### Post by mbeltagy on 2009-04-25
I was seriously upset that they killed kdvi on Jaunty. Kile, it the best latex source editor in KDE AFAIK. 
Anyway, after lots of googling. I found this suggestion by Juerg Wullschleger at

[https://bugs.launchpad.net/ubuntu/jaunty/+source/kdvi/+bug/355781](https://bugs.launchpad.net/ubuntu/jaunty/+source/kdvi/+bug/355781)

It worked for me. My steps were a bit different but the end the result is the same. 

1. edit (in sudo of course) /etc/apt/sources.list
2. add "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe multiverse" at the last line
3. run: sudo apt-get update          
4. run: sudo apt-get install kdvi

---

### Post by Juerg Wullschleger on 2009-04-26
yes, kile 2.1 crashes sometimes, but what really bothers me is that it is so slow when i am typing.

now i found a solution on:

[https://bugs.launchpad.net/ubuntu/+source/kile/+bug/361843](https://bugs.launchpad.net/ubuntu/+source/kile/+bug/361843)

start kile using

"kile --graphicssystem raster"

and it gets much faster. (i don't know if it get more unstable.)

---

### Post by lethalfang on 2009-04-26
I'm also not too trilled that they put an unstable release of Kile in the repo for Jaunty. :sad:

---

### Post by aidendeem@gmail.com on 2009-04-29
Kile does support Okular inverse search, see this bug link -
[https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/273018](https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/273018)

I installed KDVI and both forward and inverse work.

I can get inverse search to work in Okular, by setting the editor from Kate to Kile,  but I cannot get forwardDVI to work with Okular. It does open Okular, but doesnt jump to the correct line.

---

### Post by shr2004 on 2009-04-29
I installed ubuntu 9.04, then after installing kile I found its new version and disappointed by it performance from the very beginning. Even before writing a single line there, it took me a while to work out with the toolbar to make it viewable. 
I am on the verge to writing a very important document. kile is slower than my typing speed, I tried to install previous version, which was hard to find. I installed that then found icons in tool bar are not visible:confused:

So, tried texmaker, in 9.04, its even worse,. Dont know where is problem. Is it my system which was super fast and smooth in hardy.
Good to see that I am not alone with similar problem.
I am going back to windows Winedit for the moment until I find kile is stable enough not to crash and dead slow.

----------------------
Edit:
I tried the above mentioned fix and thanks a lot that is working properly

---

### Post by LillaEpsilon on 2009-04-29
I got Kile to work with Kdvi on lethalfang's advice (thanks!), and I have tried the raster graphics trick -- but Kile keeps crashing when I want it the least, plus it is still too slow.

Does anyone know if it is possible to run Kile 2.0 on Jaunty?

---

### Post by binwiederweg on 2009-04-30
thx guys,
"kile --graphicssystem raster" worked for me.!

---

### Post by lethalfang on 2009-05-01
> **LillaEpsilon said:**
> I got Kile to work with Kdvi on lethalfang's advice (thanks!), and I have tried the raster graphics trick -- but Kile keeps crashing when I want it the least, plus it is still too slow.

Does anyone know if it is possible to run Kile 2.0 on Jaunty?

Yes, I've done that. The only problem is that one of the Tool Bars doesn't show up (the most important one, which includes quick build, forward DVI, etc), so you'd have to do these things from the menu. 
Other than that, it works for now...... in the mean time, I'm waiting for the next stable release. 

[http://packages.ubuntu.com/intrepid/kile](http://packages.ubuntu.com/intrepid/kile)

---

### Post by lethalfang on 2009-05-04
Actually, the toolbar works, but you have to manually add those particular tool buttons. 

> **lethalfang said:**
> Yes, I've done that. The only problem is that one of the Tool Bars doesn't show up (the most important one, which includes quick build, forward DVI, etc), so you'd have to do these things from the menu. 
Other than that, it works for now...... in the mean time, I'm waiting for the next stable release. 

[http://packages.ubuntu.com/intrepid/kile](http://packages.ubuntu.com/intrepid/kile)

---

### Post by LillaEpsilon on 2009-05-10
Thanks for the link, lethalfang, I now have a functioning latex editor :D And I'll sign that demand for a stable release anytime.

---

### Post by useright on 2009-05-12
Could anybody tell how to set the DVI viewer to KDVI in Kile 2.1 and how to make forward and inverse search works? I have already installed Kile 2.1 and KDVI on 9.04Ubuntu.

thanks

---

### Post by lethalfang on 2009-05-13
> **useright said:**
> Could anybody tell how to set the DVI viewer to KDVI in Kile 2.1 and how to make forward and inverse search works? I have already installed Kile 2.1 and KDVI on 9.04Ubuntu.

thanks

In Kile, go to setting --> configure kile --> tools -> build

In the ViewDVI tab, replace "okular" with "kdvi."

In the LaTeX tab, replace the option with the following line:
--src-specials -interaction=nonstopmode '%source'
This line will make the KDVI do Forward Search properly. For the Quick Build option, you can choose "LaTeX + ForwardDVI" instead of "LaTeX + ViewDVI" if you want. 


To do inverse search, Ctrl - click in KDVI. Make sure your KDVI is configured to work with Kile. I think the default is Kate: go to configure KDVI and choose Kile. 

In Okular, the inverse search is Shift - click. ForwardDVI doesn't work with Okular.... at least I haven't figured it out yet.

---

### Post by sidehop on 2009-05-18
After making a serious effort to use Kile 2.1, having it crash randomly, forget keyboard shortcuts constantly, insert random "3"s in my documents... I gave up. This version is not ready for release and should not have been included in Jaunty.

Here's how I got Kile 2.0 (from Intrepid) installed quickly in Jaunty:

- Go about installing Kile 2.1 with whatever TeX-Live packages and so on (typically through Synaptic Package Manager) so that it is in working (although perhaps unstable) order.

- Use Synaptic Package Manager to uninstall Kile 2.1 while leaving the rest of your LaTeX packages in place.

- Use the deb installer found at [http://packages.ubuntu.com/intrepid/kile](http://packages.ubuntu.com/intrepid/kile)

Cheers,
Jason

---

### Post by Juerg Wullschleger on 2009-05-27
hi

kdvi works fine, but i don't need all the menus and bars, and i would like to have all the while space cut off.

the following simple perl-script that i just wrote does just that. it calls xdvi without any extras (expertmode 0) and looks into the dvi file to find out which part of the document is white. it needs xdvi and dvitype to work.

save it somewhere, for example under "~/bin/kile2xdvi.pl", and under setting --> configure kile --> tools -> build -> ForwardDVI, set Command: ~/bin/kile2xdvi.pl, Options: "%target"


cheers

juerg

```

#!/usr/bin/perl
# kile2xdvi. (c) Juerg Wullschleger, 2009

if($ARGV[0] =~ m/file:(\S*)#src:(\S*) (\S*)/){
    $dviFile = $1;
    $line = $2;
    $sourceFile = $3;
    $sourcePos = '-sourceposition "'.$line.' '.$sourceFile.'"';
}else{
    if((!$ARGV[0]) || ($ARGV[0] == "--help") || ($ARGV[0] == "-h")){
        print 'usage: kile2xdvi <dvifile> or kile2xdvi "file:<dvifile>#src:<line> <sourcefile>"'."\n";
        exit;
    }
    $dviFile = $ARGV[0];
    $sourcePos = '';
}
if (!(-e $dviFile)){
    print "$dviFile: No such file.\n";
    exit; 
}

open(DVITYPE, "dvitype $dviFile|");
$firstline = <DVITYPE>;
$minH = 300*15; $maxH = -300*3;
$minV = 300*20; $maxV = -300*3;
$dpi = 0;
#find min/max of all "hh" and "vv" in $dviFile
while (<DVITYPE>) {
    if(m/h:=(\S*)=(\S*), hh:=(\S*)/){
        if($3 < $minH){ $minH = $3; }
        if($3 > $maxH){ $maxH = $3; }
    }elsif(m/v:=(\S*)=(\S*), vv:=(\S*)/){
        if($3 < $minV){ $minV = $3; }
        if($3 > $maxV){ $maxV = $3; }

    }elsif(m/Resolution = (\S*) pixels per inch/){
        $dpi = $1;
    }
}
$offsetx = -int(100*$minH/$dpi - 10)/100; $paperx = int(100*($maxH - $minH)/$dpi + 20)/100; 
$offsety = -int(100*$minV/$dpi - 10)/100; $papery = int(100*($maxV - $minV)/$dpi + 20)/100; 
$bb = "-xoffset ".$offsetx."in -yoffset ".$offsety."in -paper +".$paperx."x".$papery."in";

$options = '-watchfile 0.5 -postscript 1 -expertmode 0 -mousemode 0 -s 6 -editor "kile --line %l %f" -nofork';
`xdvi $options $bb $sourcePos $dviFile\n`;

```

---

### Post by useright on 2009-06-10
Hi,

I am using multiple files, one main.tex and several daughter tex files, to write my thesis. But the forward search, which works on single file template, doesn't work on multiple files. The problem is similar like described here ([http://www.latex-community.org/forum/viewtopic.php?f=20&t=3380](http://www.latex-community.org/forum/viewtopic.php?f=20&t=3380))

Can anybody help?

thanks ahead

---

### Post by geops on 2009-07-27
I just down-graded it following the instructions above, Kile 2.0 works like a charm. The whole reason I switched from Fedora to Ubuntu was because I was sick and tired of dealing with unstable software.. Grrr

---

### Post by leorolla on 2009-11-02
> **mbeltagy said:**
> I was seriously upset that they killed kdvi on Jaunty. Kile, it the best latex source editor in KDE AFAIK. 
Anyway, after lots of googling. I found this suggestion by Juerg Wullschleger at

[https://bugs.launchpad.net/ubuntu/jaunty/+source/kdvi/+bug/355781](https://bugs.launchpad.net/ubuntu/jaunty/+source/kdvi/+bug/355781)

It worked for me. My steps were a bit different but the end the result is the same. 

1. edit (in sudo of course) /etc/apt/sources.list
2. add "deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) intrepid universe multiverse" at the last line
3. run: sudo apt-get update          
4. run: sudo apt-get install kdvi

Does it also allow you to force Kile to be 2.0?

---

### Post by leorolla on 2009-11-10
Hey, I got Kile 2.0 with KDVI 1.4 all integrated.

After so much pain, I found my way on Ubuntu 9.10 with Gnome Desktop:

```
sudo gedit /etc/apt/sources.list
```add to the end:
```
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted universe multiverse

```Open Synaptic:
Reload
Choose kviewshell, kdvi, kile, kbib, kbibtex, ...
Force kile to be at the Hardy version.
Apply
Lock the version of Kile, KDVI, and kviewshell
Quit
```
sudo echo 'kile hold' | sudo dpkg --set-selections
sudo aptitude hold kile
```

I don't know if I really need all that...
(I don't run many kde applications, so I didn't get any conflict yet)


Edit:

Create a file
```
sudo gedit /etc/apt/preferences.d/kile
```containing:
```
Package: kile
Pin: release a=hardy
Pin-Priority: 990
```Then whatever you do with apt-get or aptitude, they will keep good old Kile 2.0 installed :-)

---

### Post by drevicko on 2010-05-14
First I want to thank Juerg Wullschleger for his script. I'd nearly given up when I found it :confused: :P

I've updated to ubuntu 10.04 and the Kile that came with it calls itself 2.085. xdvi and kdvi havn't appeared in this ubuntu version yet, so I adapted Juerg's script to make okular work with kile. I posted it in a similar thread to this [here]("http://ubuntuforums.org/showthread.php?p=9297055#post9297055") if anyones interested.

---

### Post by yoni_m on 2010-09-16
Hi,
I found a solution the works for me with Okular and the new kile 2.08...
First lets to the kile side:
Go to:
Settings -> configure kile
choose build and then LaTeX
change the configuration from default to modern in the drop down on the to right.
This should give you a line like:
-src-specials -interaction=nonstopmode '%source'
in the text window below.

Now the Okula side:
Go to settings -> configure Okular
choose Editor and change it to kile.

Now everything should work except the inverse search is one using
Shift+click  (that is Shift and regular left click)
One more thing in Okular you must be in Browse mode (on the tool bar) for inverse search to work)

Have a good day


(Everything should be made as simple as possible but not any simpler than that)

---

### Post by qasker on 2010-09-17
Probably my remark is a bit offtopic, but I would like to say, that KDVI was very good at forward/inverse search and rendering DVI files. And one could configure forward-inverse search between KDVI and many other TeX editors (not only Kile).
I do not understand why they removed KDVI package from KDE. Okular doesn't provide same features. It doesn't even have a man page :p

---

### Post by leorolla on 2010-09-17
> **qasker said:**
> Probably my remark is a bit offtopic, but I would like to say, that KDVI was very good at forward/inverse search and rendering DVI files. And one could configure forward-inverse search between KDVI and many other TeX editors (not only Kile).
I do not understand why they removed KDVI package from KDE. Okular doesn't provide same features. It doesn't even have a man page :p

I totally agree. It's really very disappointing. It's like pushing the consequences of their political decisions on the users who rely on the software to work.

---

### Post by ADK1 on 2011-01-05
:confused:I've done everything that yoni_m said to do and I still can't get forward or inverse search working at all; nothing happens when I shift+left click in Okular, and ditto in Kile (the documentation doesn't even describe *exactly* how perform inverse search).

Is there anyone who can describe, step by step, how I might be able to get this working? It seems like an extremely useful feature. If I can get it working on my machine I will gladly write a detailed step by step guide on the matter, and submit it to whoever's in charge of documentation.

Any help is appreciated. Thanks,
A

---


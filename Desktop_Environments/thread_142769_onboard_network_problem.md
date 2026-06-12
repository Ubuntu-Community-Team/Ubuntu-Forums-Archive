---
title: "onboard network problem"
date: 2006-03-11
forum: Desktop Environments
---

### Post by ESPOiG on 2006-03-11
i have the problem of not being able to get full net resources from my modem... and at first i thought that it was prob the ip or gateway, dns or sumtin but i have tryed many things to fix it but it aint fixed yet

so i asked around and found out that this culd be todo with my gig onboard network and maybe that if i culd disable it or adjust it so it ran only at 100mb and maybe then it would work

so does anyone know how to adjust a gig card to 100mb *it is onbaord realtek or can help me with network issues cuz maybe i missed somthing

thx for anyhelp, even though the ppl that know stuff on this issue seem to be limited :D

---

### Post by Killgore on 2006-03-11
I dont think that would be a possible solution; the network would just use 10% of its full capacity.

What exactly is the problem? Slow download speeds, DNS errors? Do you have some sort of router/switch setup?

---

### Post by schdefan on 2006-03-11
Maybe the module for your network card isn't loaded. Currently my way to find out what module I need for hardware is this page [http://kmuto.jp/debian/hcl/index.cgi]("http://kmuto.jp/debian/hcl/index.cgi")
Paste the output od lspci -n and the script checks the required module. 

in a terminal and run  ```
$lsmod | grep <modulname>
```.
In your case I think the module name contains the "rlt" for realtek card.
schdefan

---

### Post by ESPOiG on 2006-03-11
well basically the problem is that i can access the interenet if i mess around with my ip, gateway and stuff

this isw wat happens * goto google... search sumtin (ubuntu forums)... shows resaults... click on link to ubuntuforums.org... page tries to load... errors out... meanwhile on my laptop right next to me with settings and everything besides it has 100mb network, can access everything fine

websites like anything but google will not load im not sure while google only loads... sumtimes yahoo and sumtimes nothing will load atall

so im at a loss as what it culd be :( if u need more detail just post

thx for any help

---


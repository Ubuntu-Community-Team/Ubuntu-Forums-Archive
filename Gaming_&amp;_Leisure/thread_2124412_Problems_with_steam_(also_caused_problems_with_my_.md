---
title: "Problems with steam (also caused problems with my laptop)"
date: 2013-03-10
forum: Gaming &amp; Leisure
---

### Post by IfMotherOnlyKnew on 2013-03-10
Hopefully someone will help me, as I had issues running games on steam(only loaded black screen), and eventually I followed some "advice" to install the mesa stack from the ubuntu wiki, then rebooted my laptop and all I see is a light blue screen. Now the details and the story how this all happened...

I was running xubuntu 12.04 LTS on the following laptop: Dell Inspiron 1545, intel core duo t6600 @ 2.20GHz (2 cpu) ~2.2GHZ(I recall linux telling me I had 2.4GHz or something like that - don't know as I can't check now) with 3GB of memory. As for the graphics card, all I know is: mobile intel 4 series express chipset family 1292mb 60hz. Sorry if this is not all what is needed, I am unable to access my specs on linux, so I had to use my brothers laptop(same one) and use dxdiag. 

Now my "story". Yesterday I was running xubuntu 11.04. Last night I upgraded to 11.10 and then to 12.04 LTS, there were no problems doing this. Earlier I install steam, update it, and nearly everything went smooth from here. I had some minor issues, nothing major, just some blob issues when steam did not close properly. Besides that, well it went well. I downloaded cs:s and once it was finally finished I attempt to play it. I of course received the error telling me to install support for S3TC, which I of course looked into. I read several discussions on steam about potential fixes. I tried using the runtime line(right word?) in the terminal and installed some packages mentioned in discussion. The packages I installed: 

```
sudo apt-get install libtxc-dxtn-s2tc0
[ "$(uname -m)" = "x86_64" ] && sudo apt-get install libtxc-dxtn-s2tc0:i386
```

Doing the above, along with: ```
force_s3tc_enable=true steam
``` I was able to "successfully" boot up cs:s, although it didn't exactly work. I tried starting it several times, only to have to close it and try again. All I would get was a black screen and see my mouse. So after this I continued to search around and found the following "advice"...

[https://wiki.ubuntu.com/Valve](https://wiki.ubuntu.com/Valve) (intel graphics)

I entered the following in terminal with no problems:

```
 sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
  sudo apt-get update
  sudo apt-get dist-upgrade
``` 

After I rebooted my computer like the instructions told me. I REALLY thought this would be the fix based off what I was reading, I didn't think this would go wrong, solely based on having an intel card. Boy was I wrong! I rebooted my computer(several times in fact) with the same result, it kept just pausing at the "intermediate" screen between logging in(showed the 12.04 LTS home(purple/orange) fine, and then just stayed there. That is now my desktop whenever I boot up. I can't do anything as far as I know. I can't enter terminal or do anything, as far as I understand. I am not the best with linux so I could really use the help!

I would GREATLY APPRECIATE someone helping me out with this. I was really looking forward to being able to play some great games on steam on the go, and most importantly I need this laptop functioning for school. I know my current situation is more of a "linux problem", versus a steam one, although I was in the process of following suggested advice to getting steam working, and now my computer is all weird.

Like I said before, I would greatly appreciate any advice how to begin fixing my problem, and if you need ANY more information(hardware etc) just let me know, I will do my best to obtain it.

Thank You!

---


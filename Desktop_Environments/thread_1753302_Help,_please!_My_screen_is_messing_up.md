---
title: "Help, please! My screen is messing up"
date: 2011-05-08
forum: Desktop Environments
---

### Post by After89 on 2011-05-08
I just installed Ubuntu 11.04 today. I used to run windows vista but i got the blue screen of death, so a friend told me to install ubuntu. It was love at first sight, and i will continue to use this OS now. But lets talk about the annoying problem i have. I dont know how to explain it but i will try. On my screen there are many many blue slim lines that travels fast from top to bottom all the time, they move fast and messes up the graphics, I have tried to search the problem on google but i have no idea what the search for. But all I can say is that its these flickering slim blue lines that are constently moving and flashing, i can see them very clear the darker the screen are. If someone can help me I would be very grateful.

Btw, when I take a screenshot of the desktop the bug does not show in the picture.

Here is a picture-link of the problem:
[http://postimage.org/image/29qkkzehw/999359ef/](http://postimage.org/image/29qkkzehw/999359ef/)

Thanks 

Awesome forum btw!!

---

### Post by 23dornot23d on 2011-05-08
Take a photo with a camera and post it ....

What graphics card and what computer is this on please ......

---

### Post by After89 on 2011-05-09
> **23dornot23d said:**
> Take a photo with a camera and post it ....

What graphics card and what computer is this on please ......

Hi!

I have a HP Pavilion dv6-1100eo with ATI Radeon graphic card.

Here is the photo : [http://postimage.org/image/29qkkzehw/999359ef/](http://postimage.org/image/29qkkzehw/999359ef/)

Thanks bud ;)

---

### Post by 23dornot23d on 2011-05-09
What do these commands give you back please ...... if you enter them into a terminal.

sudo dmidecode -s system-product-name && sudo dmidecode -s system-version

and then ......

lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA


There is a video here [COLOR=Red]** [I found on video switching]("http://www.youtube.com/watch?v=-S5-BVFk0G0")**[/COLOR]  not sure if this will help you or not but it
may be worth a try to use one mode or the other depending which works best for you.

( I use Nvidia on all my systems )...... but any information you supply here may help others
with ATI cards to give you some help on this matter ........

I did a lot of searching on the net to try to identify problems and solutions but there is 
limited information and a few bugs with the switching ..... but little on the problem you are facing

Searches I Tried out .....

[linux Pavilion dv6-1100eo ati graphics driver]("http://www.google.com/search?client=ubuntu&channel=fs&q=Pavilion+dv6-1100eo+ati+graphics&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&hs=mwk&channel=fs&source=hp&q=linux+Pavilion+dv6-1100eo+ati+graphics+driver&aq=f&aqi=&aql=&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=9ecd9e91e08e01f")

It could be this ..... ATI card (4650) ...... but to confirm cut and paste the command I gave .....
 into a terminal and press enter .... then post the results ..... 

[linux Pavilion dv6-1100eo ati 4650]("http://www.google.com/search?client=ubuntu&channel=fs&q=Pavilion+dv6-1100eo+ati+graphics&ie=utf-8&oe=utf-8#sclient=psy&hl=en&client=ubuntu&channel=fs&source=hp&q=linux+Pavilion+dv6-1100eo+ati+4650&aq=f&aqi=&aql=f&oq=&pbx=1&bav=on.2,or.r_gc.r_pw.&fp=9ecd9e91e08e01f")

[B]lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA

as an example mine shows this information

[/B]> 
keith@keith-laptop:~$ lspci -vnnn | perl -lne 'print if /^\d+\:.+(\[\S+\:\S+\])/' | grep VGA
01:00.0 VGA compatible controller [0300]: nVidia Corporation G98 [GeForce 9300M GS] [10de:06e9] (rev a1) (prog-if 00 [VGA controller])
keith@keith-laptop:~$ 



---


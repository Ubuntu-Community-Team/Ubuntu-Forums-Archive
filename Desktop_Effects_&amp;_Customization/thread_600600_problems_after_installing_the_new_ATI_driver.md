---
title: "problems after installing the new ATI driver"
date: 2007-11-02
forum: Desktop Effects &amp; Customization
---

### Post by Zakk Walid on 2007-11-02
I installed the new ATI Driver. 
The effects work gr8 even better than before! 
But when i play a 3D game, or google earth ect'.. i have a black screen kinda flashing during the game or whatever.... 
And when i opend a video, my desktoped effects got disabled :| 

then... 
I disabled the desktop effects and everything workd gr8! games, apps, videos.. 

How can i solve this problem ? 
this driver shpuld work with my card perfectly as i saw on a website.
as far as i know the problem is with compiz...(?)

thank you =]

---

### Post by jimerickso on 2007-11-02
for video play back use:

mplayer -vo x11 /path/to/video

---

### Post by jimerickso on 2007-11-02
if you are using vlc set the video driver to xshm.

---

### Post by Zakk Walid on 2007-11-03
thank you =] 

but u know S: 
it's still not solving my games/apps problems =[

---

### Post by kshane on 2007-11-03
> **Zakk Walid said:**
> thank you =] 

but u know S: 
it's still not solving my games/apps problems =[

Are you using AIGLX or GLX?

Kevin

---

### Post by Zakk Walid on 2007-11-03
i disabled my glx then i deleted it. 
i just installed the new ATI driver ==> now i have just AIGLX. 

should i instal glx again :O ? will it solve the problem?

---

### Post by kshane on 2007-11-03
> **Zakk Walid said:**
> i disabled my glx then i deleted it. 
i just installed the new ATI driver ==> now i have just AIGLX. 

should i instal glx again :O ? will it solve the problem?

I think you should be good to go...

---

### Post by kshane on 2007-11-03
> **Zakk Walid said:**
> i disabled my glx then i deleted it. 
i just installed the new ATI driver ==> now i have just AIGLX. 

should i instal glx again :O ? will it solve the problem?

If you're not working right, try this HOWTO after the installation bit.  There are a few mods that need to be made to xorg.conf, if they aren't already there.

[http://ubuntuforums.org/showthread.php?t=589075](http://ubuntuforums.org/showthread.php?t=589075)

---

### Post by Zakk Walid on 2007-11-03
> **kshane said:**
> If you're not working right, try this HOWTO after the installation bit.  There are a few mods that need to be made to xorg.conf, if they aren't already there.

[http://ubuntuforums.org/showthread.php?t=589075](http://ubuntuforums.org/showthread.php?t=589075)

i worked with this tutorial, did it again, and still dosent work... hmm... 

should i instal Xserve? (the XGL thing :S )

---

### Post by kshane on 2007-11-03
> **Zakk Walid said:**
> i worked with this tutorial, did it again, and still dosent work... hmm... 

should i instal Xserve? (the XGL thing :S )

Which ATI card do you have?  How old is it?

What method did you use to install it?  

I would suggest just using the following to install:

```

sudo bash ./ati-driver-installer-8.42.3-x86.x86_64.run

```

Use the ATI installer to set up.  It worked better for me than any other HOWTO...

Then follow the other instructions on the link to be sure your xorg.conf is set correctly.

---

### Post by Zakk Walid on 2007-11-03
> **kshane said:**
> Which ATI card do you have?  How old is it?

What method did you use to install it?  

I would suggest just using the following to install:

```

sudo bash ./ati-driver-installer-8.42.3-x86.x86_64.run

```

Use the ATI installer to set up.  It worked better for me than any other HOWTO...

Then follow the other instructions on the link to be sure your xorg.conf is set correctly.

i have radeon 9600
2-3 years :| 
 method 2 ofcours

and i did what u have toled me and when i login to ubuntu i see everything white and i cant use nothing... i got in my ubuntu now on a safemode of something like that and i am folowing the tutorial from the begining :S

i cant install using the old  way coz i m using this safemode thing so it is locking some files :'(

---


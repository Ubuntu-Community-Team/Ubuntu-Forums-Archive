---
title: "New to Ubuntu- Help needed with Beryl"
date: 2007-04-06
forum: Desktop Effects &amp; Customization
---

### Post by Tim_06 on 2007-04-06
Hello.

First off I am not new with computers, I am just new to Ubuntu. 

I had no trouble installing Ubuntu, but I cant seem to be able to figure how to install Beryl. 

I need some major help here. 

I was wondering if someone is willing to take some time and help me through the steps.

You can either respond here or Pm me.

Thanks a lot.

Cheers Tim

---

### Post by theninthdimension on 2007-04-06
Tim,

     I just installed Beryl today using the guide at this link: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

     As they say, just remember that Beryl is in beta release, so be careful.

Jeff.

---

### Post by Zuuswa on 2007-04-06
Well, from a fresh install of Ubuntu, there are a few steps along the way to a beautiful Beryl desktop.  First you need to install new drivers for your video card.  If you search for a program called Envy, that will probably be the easiest route for a beginner.  Then, if you have an Ati card, you will have to set up an Xgl session, but if I remember correctly the new Nvidia drivers dont require them, but I could be wrong.  Then you can install Beryl.

Envy: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
XGL Setup: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL) (this is for feisty, but pertinent info and links for edgy)

---

### Post by Tim_06 on 2007-04-06
Hey 

I tried to install Envy. Then is thing pops up that says "Error: Dependency is not satisfiable: module-assistant"

So with that being said it wont let me install the package. 

Any help here ?

Cheers Tim

---

### Post by lukew on 2007-04-06
> **Tim_06 said:**
> Hey 

I tried to install Envy. Then is thing pops up that says "Error: Dependency is not satisfiable: module-assistant"

So with that being said it wont let me install the package. 

Any help here ?

Cheers Tim

Have you tried installing module-assistant? I presume that you are installing envy from a downloaded package and not from a repository?

---

### Post by Tim_06 on 2007-04-06
How do I download a module-assistant ?

cheers Tim

---

### Post by reclusivemonkey on 2007-04-07
Erm, steady on here people. We've not even asked Tim what kind of graphics card he has. Also, its not necessary to use Envy just to get a Nvidia driver, the one in the repos will do fine. 

Tim;

1. What make/model of graphics card do you have?

2. What version of Ubuntu are you using?

---

### Post by lukew on 2007-04-07
> **Tim_06 said:**
> How do I download a module-assistant ?

cheers Tim

You can do this from the terminal.

```
sudo apt-get install module-assistant 
```


or through synaptec package manager. Whatever sails ya boat.

---

### Post by Tim_06 on 2007-04-07
Hello

Well first off im using Ubuntu 6.10

I can't remember what type of graphics card I have. How can I find this out ?

When I type that module thing in to the terminal this happens

root@tim-desktop:~# sudo apt-get install module-assistant
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package module-assistant
root@tim-desktop:~# 

hope that helps

Tim

---

### Post by reclusivemonkey on 2007-04-07
Hi Tim,

At a terminal, (Applications Menu, Accessories, Terminal) type the following;

```

lspci | grep VGA

```

and paste the results back here (if you have a wheel mouse, you can highlight the command above, then in your terminal, click the wheel mouse, and it will paste the text).

---

### Post by Tim_06 on 2007-04-07
Hey

Here was the response  

root@tim-desktop:~# lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)
root@tim-desktop:~# 


so it looks like I have a nVida

hope that helps 

tim

---

### Post by reclusivemonkey on 2007-04-07
Yep, that's right you have a Nvidia card. Its also supported by the regular nvidia drivers and should work fine with Beryl. I suggest you follow the Edgy Wiki to get Beryl working. I followed these steps when I used Edgy and it all worked fine;

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Beryl.2FAIGLX_.28Nvidia.29)

There are a lot of tip on that page to do various things in Edgy, you may want to look at some of the others too. Good Luck =]

---

### Post by Tim_06 on 2007-04-07
Hey.

I got up to the step install Beryl than this happens.

root@tim-desktop:~# sudo apt-get install beryl emerald-themes
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package beryl
root@tim-desktop:~# 


what can I do ?

thanks Tim

---

### Post by reclusivemonkey on 2007-04-07
Did you read the section about adding extra repsoitories?

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

Sorry Tim, I don't do support via PMs or MSN, I have a nine month old baby who requires too much attention!

---

### Post by barath on 2007-04-12
I also want to configure my nvidia driver when i typed 

             lspci | grep VGA
              
               nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
i got this back what does this mean?

---

### Post by reclusivemonkey on 2007-04-12
> **barath said:**
> I also want to configure my nvidia driver when i typed 

             lspci | grep VGA
              
               nVidia Corporation NV18 [GeForce4 MX 4000 AGP 8x] (rev c1)
i got this back what does this mean?

It means you have a nVidia GeForce4 MX4000 card. If you need support, I would advise you to start your own thread, but please search the forums there are hundreds of Beryl threads.

---


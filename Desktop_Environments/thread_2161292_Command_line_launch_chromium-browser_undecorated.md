---
title: "Command line launch chromium-browser undecorated"
date: 2013-07-10
forum: Desktop Environments
---

### Post by stephaneeybert on 2013-07-10
Hi,

I would like to see the chromium-browser being launched undecorated when typing the chromium-browser command in a terminal.

Thanks.

---

### Post by stephaneeybert on 2013-07-10
Here is my autostart entry to which I would like to add an undecorate option.

[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Chromium
Comment=The Chromium web browser
Exec=/usr/bin/chromium-browser %U --maximize
Hidden=false
NoDisplay=false
Terminal=false

---

### Post by vasa1 on 2013-07-10
Hi, your thread has been tagged "lubuntu". If that's intentional, then you can make use of ~/.config/openbox/lubuntu-rc.xml. The applications section allows you to specify which program you wish to start decorated. That section is well commented and the comments are quite explanatory. If you need further help, do ask.

BTW, both Google Chrome and Chromium use specific switches listed very nicely over here: [http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/). I'm saying this because instead of just "--maximize", you may want to use "--start-maximized"

So, I would rather have 

Exec=/usr/bin/chromium-browser --start-maximized %U (with the %U at the very end)

---

### Post by stephaneeybert on 2013-07-10
Thanks for that input !

I looked into the list of options at [http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/) but could not find the one that would undecorate the window.

You would know its name ?

I shall also try to have the option
<decor>no</decor>
in the .config/openbox/lubuntu-rc.xml file.

---

### Post by vasa1 on 2013-07-10
> **stephaneeybert said:**
> Thanks for that input !

I looked into the list of options at [http://peter.sh/experiments/chromium-command-line-switches/](http://peter.sh/experiments/chromium-command-line-switches/) but could not find the one that would undecorate the window.

You would know its name ?

I shall also try to have the option
<decor>no</decor>
in the .config/openbox/lubuntu-rc.xml file.

AFAICT, there isn't an undecorate option, *per se*, to be used in the Exec line (unlike --start-maximized). You need to do this in lubuntu-rc.xml.
Alternatively, if you don't wish to be tied down, you could just toggle decorations on or off using Alt+Spacebar, d (the "d" key) for any window at any time.

---

### Post by stephaneeybert on 2013-07-10
I updated the option to have it as
<decor>no</decor>
in the .config/openbox/lubuntu-rc.xml file and rebooted the system.

But on logging in, all the windows, including the Chromium one, are decorated.

---

### Post by vasa1 on 2013-07-10
> **stephaneeybert said:**
> I updated the option to have it as
<decor>no</decor>
in the .config/openbox/lubuntu-rc.xml file and rebooted the system.

But on logging in, all the windows, including the Chromium one, are decorated.

Could you please copy paste what you have done over here? Please include a little before (and after) for context!

---

### Post by vasa1 on 2013-07-10
Also take a look at this: [https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized](https://help.ubuntu.com/community/Lubuntu/Windows#Launching_Windows_Maximized)

If that link gives you a massive headache, you may look at a GUI approach (but you'll have to install the necessary software): [http://askubuntu.com/a/306256/25656](http://askubuntu.com/a/306256/25656)

---

### Post by stephaneeybert on 2013-07-10
Sure, I just replaced the yes by a no as in:
>     # each rule element can be left out or set to 'default' to specify to not 
    # change that attribute of the window

    <decor>no</decor>
    # enable or disable window decorations

    <shade>no</shade>
    # make the window shaded when it appears, or not


---

### Post by vasa1 on 2013-07-10
> **stephaneeybert said:**
> Sure, I just replaced the yes by a no as in:

Okay, but that's not enough. Please take a look at the wiki link I provided.

---

### Post by stephaneeybert on 2013-07-10
Hi Vasa,

Sorry for my light head today, I didn't see my setup with sitting in a commented out section :-)

I now have it like this:
>     <application type="normal">
      <maximized>true</maximized>
      <decor>no</decor>
    </application>


And it works perfectly as you said.

All the windows are now maximized and undecorated.

Thank you !

---

### Post by vasa1 on 2013-07-10
> **stephaneeybert said:**
> ...

All the windows are now maximized and undecorated.

Thank you !
You're welcome! The wiki also explains how you can make **only** specific applications open undecorated/maximized if needed.

---


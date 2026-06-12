---
title: "Beryl on HP laptop --&gt; Fatal error"
date: 2007-04-02
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-04-02
Installed Edgy on new HP Pavilion dv1000 laptop a few days ago without problems.
Next step was to install Beryl (which I have previously done with success on two desktops).
The laptop has an Intel 945G video card and I used this [guide]("http://doc.gwos.org/index.php/BerylOnEdgy").
Everything seemed to go smoothly during the install but when I typed 
```
beryl-manager
```
to get the show on the road, it went to the login page and no beryl icon showed in the panel when the desktop eventually appeared.
Beryl manager and Emerald themes were available as options in Applications. However, clicking on Berl Manager again just brought me to the login page and no beryl effect were available on restart.
Then I made an unforgivable error. I put Beryl-Manager in the Starting Sessions.
As a result, now when I start Ubuntu I'm brought back to the login page continuously.
So now I have two problems:
1) How do I get the Beryl-Manager out of Starting Sessions from TTY1 ?
2) Having done that, any idea why Beryl is apparently not happy on this laptop ?

Thanks
Paul

---

### Post by aeortiz on 2007-05-10
You're not alone,

  My dv1000 is in similar trouble, Ive tried many how-to's once destroying my graphics settings so badly that I couldn't even enter Kubuntu in graphical mode, and had to restore a previous version of my xorg.conf file. If you find a solution to this, please let me know! my email is aeortiz (at) iname.com.

thanks,

Aaron Ortiz

Ps. I've tried to get Beryl working on Edgy and Feisty, to no avail

---

### Post by blazercist on 2007-05-10
Are you sure you have you graphics card driver installed properly and 3d acceleration is functioning? Post your xorg.conf.

This guide works if you read it first and pay attention. [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by PaulFXH on 2007-05-11
@aeortiz
Yes, I very quickly got over the problem I had with Beryl not working on that laptop.
I did just two things:
1) Install 915resolution from Synaptic
2) Change the graphics card driver in /etc/X11/xorg.conf from "vesa" to "i810"

Assuming that your dv1000 has the same Intel945GM card as mine, then maybe this could work for you as well.
Good luck

---


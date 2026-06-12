---
title: "VirtualBox, XP(host), Intrepid Ibex(guet)"
date: 2008-11-09
forum: Desktop Environments
---

### Post by kidguayas on 2008-11-09
Hello Ubuntu community;
    I would like to express how happy I am with all your hard work. Due to some extraneous hardware failure, I cannot format ext3 and install Ubuntu 8.10. I have to run my machine on XP and use VirtualBox 2.0.4 to run Linux. I have install guess additions and this solve screen resolution problems and with your guide and VirtualBox manuals I have installed the USB. However, I cannot do shared folder between XP host and Intrepid Ibex guest. Could anyone point to me on the right direction to fix this inconvinience?

Thanks,

Carlos X Rosado

PS.  Sorry for making this post so long and detailed but I assume that someone might have similar issues. So if they cannot find solutions for the screen resolution and USB I will more than happy to point them out in a right direction.

---

### Post by Vadi on 2008-11-09
Firstly, have you heard of [Wubi]("http://wubi-installer.org/")? It uses your windows partition to run a native ubuntu. 

If that cannot work, what problem exactly are you having when sharing folders?

---

### Post by kidguayas on 2008-11-09
Thanks for your help on this matter. I did try Wubi before and it did not work for me. 
 I have also tried to set it up as instructed on the manual VirtualBox2.0.4 section 4.6 Linux guest. However, I have not been able to see what I have place in either side XP host or Ubuntu 8.10 guest. If you have any suggestions and how to set it up or a step by step manual that I can follow, I will be very thankful.

This is what I have tried so far:

sudo mkdir ubuntu

then

sudo mount -t vboxsf ubuntu /media/share

I get this message:

/sbin/mount.vboxsf: mounting failed with the error: No such device

What am I doing wrong?
Also what can I do to make it run when it boots.
Back to top 	
View user's profile Send private message

---

### Post by 081103jk on 2008-11-10
&#30417;&#25511;&#20013;&#24515;&#24314;&#35774;&#65292;&#30417;&#25511;&#20013;&#24515;&#38656;&#23545;&#21069;&#31471;&#21508;&#20010;&#30417;&#25511;&#28857;&#36827;&#34892;&#23454;&#26102;&#35270;&#39057;&#30417;&#35270;&#21450;&#24405;&#20687;&#65292;&#26082;&#35201;&#23454;&#29616;&#35270;&#39057;&#20449;&#21495;&#30340;&#35760;&#24405;&#65292;&#21516;&#26102;&#20063;&#35201;&#23454;&#29616;&#35270;&#39057;&#30417;&#30475;&#21450;&#35270;&#39057;&#23384;&#20648;&#65292;[**&#30417;&#25511;**](http://www.cydjk.com/jk.htm)&#22240;&#27492;&#38656;&#32473;&#27492;&#20013;&#24515;&#37197;&#32622;&#27427;&#26234;&#24658;&#22823;&#22411;&#31649;&#29702;&#36719;&#20214;&#12290;&#22823;&#20013;&#22411;&#32593;&#32476;&#35270;&#39057;&#30417;&#25511;&#31649;&#29702;&#24179;[**&#30417;&#25511;**](http://www.cydjk.com/jk.htm)&#21488;&#36719;&#20214;&#26159;&#19987;&#38376;&#38024;&#23545;&#22823;&#20013;&#22411;&#32593;&#32476;&#29615;&#22659;&#19979;&#20998;&#25955;&#30417;&#25511;&#22330;&#25152;&#19981;&#21516;&#31181;&#31867;&#25968;&#23383;&#22270;&#35937;&#35774;&#22791;[**&#30417;&#25511;**](http://www.cydjk.com/jk.htm)&#12289;&#23433;&#38450;&#25253;&#35686;&#35774;&#22791;&#38598;&#20013;&#30417;&#25511;&#31649;&#29702;&#30340;&#19987;&#29992;&#24179;&#21488;&#36719;&#20214;,&#26159;&#19968;&#31181;&#20840;&#25968;&#23383;&#21270;&#12289;&#22522;&#20110;&#32593;&#32476;&#21644;&#39640;&#24230;&#38598;&#20013;&#31649;&#29702;&#30340;&#31532;&#19977;&#20195;&#23433;&#38450;&#31649;&#29702;&#24179;&#21488;&#36719;&#20214;. &#20197;&#28385;&#36275;&#34892;&#19994;&#23458;&#25143;&#39640;&#21487;&#38752;&#24615;&#12289;&#22797;&#26434;&#24615;&#21644;&#28789;&#27963;&#24615;&#30340;&#35270;&#39057;&#19982;&#23433;&#38450;&#30417;&#25511;&#19994;&#21153;&#31649;&#29702;&#38656;&#27714;&#20026;&#20027;&#35201;&#30446;&#30340;&#65292;&#36866;&#29992;&#20110;&#22823;&#20013;&#22411;IP&#32593;&#32476;&#35270;&#39057;&#30417;&#25511;&#29615;&#22659;&#19979;&#23545;&#19981;&#38480;&#36335;&#25968;&#30340;PC&#26550;&#26500;DVR&#12289;[**&#30417;&#25511;**](http://www.cydjk.com/jk.htm)&#23884;&#20837;&#24335;DVR&#12289;DVS&#12289;IP&#25668;&#20687;&#26426;&#21644;&#25253;&#35686;&#35774;&#22791;&#30340;&#29992;&#25143;&#35282;&#33394;[**&#30417;&#25511;**](http://www.cydjk.com/jk.htm)&#12289;&#35774;&#22791;&#37197;&#32622;&#12289;&#25253;&#35686;&#20851;&#32852;&#31574;&#30053;&#12289;&#33258;&#23450;&#20041;&#20219;&#21153;&#12289;&#30005;&#23376;&#22320;&#22270;&#12289;&#27969;&#23186;&#20307;&#36716;&#21457;&#12289;&#38598;&#20013;&#23384;&#20648;&#12289;&#32593;&#32476;&#25968;&#23383;&#30697;&#38453;&#12289;&#35270;&#35759;&#20250;&#35758;&#31561;&#30340;&#38598;&#20013;&#30417;&#25511;&#19982;&#23433;&#38450;&#31649;&#29702;&#12290;&#37319;&#29992;&#20102;J2EE&#12289;&#24494;&#26680;&#24515;&#21152;&#25554;&#20214;&#12289;WebSERVICE&#12289;WEB2.0&#12289;O/R MAPPING&#12289;AOP&#12289;LDAP&#12289;SSO&#31561;&#20808;&#36827;&#25216;&#26415;&#21644;&#26550;&#26500;&#65292;&#36719;&#20214;&#26356;&#21152;&#31283;&#23450;&#12289;&#23433;&#20840;&#12289;&#20581;&#22766;&#12289;&#24320;&#25918;&#65292;&#33021;&#22815;&#28385;&#36275;&#24403;&#21069;&#38134;&#34892;&#12289;&#31038;&#20250;&#27835;&#23433;&#12289;&#20132;&#36890;&#12289;&#36890;&#20449;&#12289;&#30005;&#21147;&#12289;&#26657;&#22253;&#12289;&#38081;&#36335;&#31561;&#22810;&#20010;&#34892;&#19994;&#30340;&#36328;&#21306;&#22495;&#22823;&#20013;&#22411;&#32593;&#32476;&#35270;&#39057;&#19982;&#23433;&#38450;&#30417;&#25511;&#39046;&#22495;&#30340;&#21508;&#31181;&#38656;&#27714;&#21644;&#26410;&#26469;&#38598;&#25104;&#21040;&#34892;&#19994;&#22823;&#20449;&#24687;&#31649;&#29702;&#31995;&#32479;&#20013;&#30340;&#38656;&#27714;

---

### Post by Vadi on 2008-11-11
As a last chance, give Wubi a try again - a new version was out with the 8.10 release ([http://wubi-installer.org/](http://wubi-installer.org/)). It's easier to setup and works much better than ubuntu in a virtual machine.

But, if that doesn't work, here's how you can install the guest additions on the ubuntu guest and setup a shared folder.

Go to Devices - Install Guest additions.


Wait a while, and then this will come up: [[img]http://www.ubuntu-pics.de/thumb/5504/screenshot_16_8VHAjT.png[/img]](http://www.ubuntu-pics.de/bild/5504/screenshot_16_8VHAjT.png)

In the virtual machine, go to applications - accessories - terminal: [[img]http://www.ubuntu-pics.de/thumb/5505/screenshot_17_HncPnT.png[/img]](http://www.ubuntu-pics.de/bild/5505/screenshot_17_HncPnT.png)

Type "sudo " in the terminal, and then drag the *VBoxLinuxAdditions-x86.run* file into it: [[img]http://www.ubuntu-pics.de/thumb/5506/screenshot_18_1A6Bhc.png[/img]](http://www.ubuntu-pics.de/bild/5506/screenshot_18_1A6Bhc.png) and [[img]http://www.ubuntu-pics.de/thumb/5507/screenshot_19_99jDzg.png[/img]](http://www.ubuntu-pics.de/bild/5507/screenshot_19_99jDzg.png)

Press enter, type in your ubuntu password if needed, and wait a bit while it builds the stuff it needs. Restart your ubuntu after it's done.

Now we can setup the shared folders.

Go to devices - shared folders... [[img]http://www.ubuntu-pics.de/thumb/5508/screenshot_20_6r40PH.png[/img]](http://www.ubuntu-pics.de/bild/5508/screenshot_20_6r40PH.png)

Now, here you can add folders that you'd like shared. Click on the button that looks like a folder with a plus on it: [[img]http://www.ubuntu-pics.de/thumb/5509/screenshot_21_X25N4e.png[/img]](http://www.ubuntu-pics.de/bild/5509/screenshot_21_X25N4e.png)

In this dialog, enable the "Make Permanent" option, and then press the down button by folder path and select Other: [[img]http://www.ubuntu-pics.de/thumb/5510/screenshot_22_cH30dy.png[/img]](http://www.ubuntu-pics.de/bild/5510/screenshot_22_cH30dy.png)

Go and find the folder you'd like to share, press Open, and the path will get filled in for you. Make sure to remember the Folder Name it gives you - or change it if you'd like, but you'll need this folder name later on.

Press OK and OK on the two dialogs.

Now, we need to get Ubuntu to see the shared folder. In your Ubuntu home folder (click on Places - Home Folder to get to it), make a folder called "share". Then, open the terminal, and paste this command in:

> sudo mount -t vboxsf *Folder Name* ~/share

Replace *Folder Name* with the one you were supposed to remember above.

Now if the magic worked, your "share" folder in Ubuntu should see the same stuff the folder contains on Windows.

Let me know if you run into any difficulties during this, I'd be glad to help.

---

### Post by kidguayas on 2008-11-11
Thanks everyone for your help. I figured what I was doing wrong and I am posting a solution for the next person that has a similar problem.

This step might be kind of obvious for a lot of people, but it was not for me.

1. sudo apt-get install build-essential

2. then add the guest additions as indicated in the manual section 4

3. create a directory if you want 

   sudo mkdir /mnt/windowsxp

This step can be avoid as long as you know exactly where is the folder that you want to share

4. sudo mount -t vboxsf ubuntu /mnt/windowsxp

*ubuntu is the name of the folder that I created in Windows XP and I decided to share.

5. This step is not necessary, but I got a lot of references from previous versions of virtualbox, so you might need it.
This is to start the sharing at booting or something like that:

sudo gedit /etc/fstab

Add this line

ubuntu /mnt/windowsxp vboxsf rw,uid=1000,gid=1000 0 0

that is it!

---

### Post by Vadi on 2008-11-11
Glad you got it working.

---

### Post by jjunju on 2009-09-19
what do the options > vboxsf rw,uid=1000,gid=1000 0 0 mean? In another tutorial i saw they used something like this > vboxsf none 0 0 so I am confused on how to go forward editing the /etc/fstab in order to make my mount permanent.

I must choose between
> D_DRIVE /media/hdd vboxsf rw,uid=1000,gid=1000 0

and 

> 
D_DRIVE /media/hdd vboxsf none 0 0

What is the difference? Thanks. Appreciate any help!!

---


---
title: "Kubuntu freeze at change to PageOne"
date: 2012-10-23
forum: Desktop Environments
---

### Post by grusty on 2012-10-23
I made a fresh install of Kubuntu 12.10 (I had Kubuntu 12.04).

I have a netbook Lenovo S10-2. I use netbook-plasma environment with a kubuntu-low-fat-settings file installed.

At do click over PageOne, Kubuntu freeze. This is a bug, at is commented at Problems Know at Kubuntu page.

At bug site say "Remove Opendesktop applet from netbook config".
[https://bugs.launchpad.net/ubuntu/+source/kdeplasma-addons/+bug/1066861](https://bugs.launchpad.net/ubuntu/+source/kdeplasma-addons/+bug/1066861)

My question is, About what file they are talking?

---

### Post by greyspammer on 2012-10-28
I had a similar problem.

Here's how I fixed it: In the file ~/.kde/share/config/plasma-netbook-appletsrc, I searched for "opendesktop".

I got a hit like this:
```

[Containments][9][Applets][12]
immutability=1
plugin=opendesktop

[Containments][9][Applets][12][Configuration]
geoCity=\s(Unknown city)
geoCountry=PRIVATE
geoCountryCode=XX
geoLatitude=0
geoLongitude=0

[Containments][9][Applets][12][LayoutInformation]
Column=1
Order=0

```I stopped KDE completely ("service lightdm stop" on a text console), removed those entries above (all sections starting with "[Containments][9][Applets][12]") and started lightdm again ("service lightdm start"). After that, I could switch to "Page One". It still had some empty applet on it. But I then were able to click on the Plasma icon in the lower left corner and completely remove the page.

Back on the "Start and launch" page, I simply added a new "Page One". The new page is empty and without those nasty social media BS choked down your throat. You can then configure it as you wish (I suggest to stay away from the OpenDesktop stuff though ;)).

There might be an easier way but now it's fixed for me.

hth

---

### Post by grusty on 2012-10-29
Great !! I made it.
Now all works fine. Thank a lot. Is nothing hard, but is a little ennofing.

I like Kubuntu at my netbook. Just a little isse with java ant gwenview, in other tread. But step by step. 

Thanks ! :D

---

### Post by pdc_romeo on 2013-03-01
Sorry to ask... (I am new on Kubuntu) 

Can you explain step by step to resolve this on Kubuntu... 
(I'm confusing about how to stop and start on text console...)
Thank's

---

### Post by mparillo on 2013-03-01
> **pdc_romeo said:**
> Sorry to ask... (I am new on Kubuntu) 

Can you explain step by step to resolve this on Kubuntu... 
(I'm confusing about how to stop and start on text console...)
Thank's

[COLOR=#222222]I had this bug:
[https://bugs.launchpad.net/kdeplasma-addons/+bug/1066861](https://bugs.launchpad.net/kdeplasma-addons/+bug/1066861)
And I resolved it by going to the 13.04 Daily Builds.[/COLOR]

---

### Post by pdc_romeo on 2013-03-06
Finally I know how to start or stop service lightdm... and edit plasma-netbook-appletsrc... but page one still freeze... even I already restart... please anybody help...

Thank's

---

### Post by lalit0611 on 2013-03-07
Same problem with me. Page one still freezes most of the times. Sometimes at random it starts working. Please help.
Thanks

---

### Post by Yochanan on 2013-06-16
> **greyspammer said:**
> I had a similar problem.

Here's how I fixed it: In the file ~/.kde/share/config/plasma-netbook-appletsrc, I searched for "opendesktop".

I got a hit like this:
```

[Containments][9][Applets][12]
immutability=1
plugin=opendesktop

[Containments][9][Applets][12][Configuration]
geoCity=\s(Unknown city)
geoCountry=PRIVATE
geoCountryCode=XX
geoLatitude=0
geoLongitude=0

[Containments][9][Applets][12][LayoutInformation]
Column=1
Order=0

```I stopped KDE completely ("service lightdm stop" on a text console), removed those entries above (all sections starting with "[Containments][9][Applets][12]") and started lightdm again ("service lightdm start"). After that, I could switch to "Page One". It still had some empty applet on it. But I then were able to click on the Plasma icon in the lower left corner and completely remove the page.

Back on the "Start and launch" page, I simply added a new "Page One". The new page is empty and without those nasty social media BS choked down your throat. You can then configure it as you wish (I suggest to stay away from the OpenDesktop stuff though ;)).

There might be an easier way but now it's fixed for me.

hth

After stopping lightdm I can't do anything at all. How does one keep Kate & Konsole open after doing that? I tried deleting said entries (via "sudo kate"), saving & rebooting but no go. This still happens in 13.04, hence the thread resurrection.

---


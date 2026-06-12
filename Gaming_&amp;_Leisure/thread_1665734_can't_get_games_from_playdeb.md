---
title: "can't get games from playdeb"
date: 2011-01-12
forum: Gaming &amp; Leisure
---

### Post by mystmaiden on 2011-01-12
I have been trying for a couple of days to download a few games off playdeb, they show up in synaptic but I get an error.

```
W: Failed to fetch http://mirror.anl.gov/pub/ubuntu/pool/universe/s/sdl-image1.2/libsdl-image1.2_1.2.10-1_i386.deb
  404  Not Found
```This has happened so far with zaz, frozen bubble and frogatto, even though I successfully loaded zaz and frozen for 9.10 just the other day. I'm using 10.04 now, but Frogatta does say its available for that distro.

I'd love some suggestions.

thanks,

mystmaiden

---

### Post by Vadi on 2011-01-12
Only 10.10 is really supported. Check what version the app is available for on getdeb.net

---

### Post by Vadi on 2011-01-12
doublepost

---

### Post by thatguruguy on 2011-01-12
> **Vadi said:**
> Only 10.10 is really supported. Check what version the app is available for on getdeb.net

That's simply incorrect.

> **mystmaiden said:**
> This has happened so far with zaz, frozen  bubble and frogatto, even though I successfully loaded zaz and frozen  for 9.10 just the other day. I'm using 10.04 now, but Frogatta does say  its available for that distro.


Is this on the same computer? Have you recently updated from 9.10 to 10.04?  If so, you need to make sure you have the correct repository enabled for getdeb/playdeb.  Have you tried to install (or reinstall) the repository as directed on the playdeb site?

---

### Post by mystmaiden on 2011-01-13
Thanks for the replies, two out of three of the games I mentioned list 10.04.

Frozen Bubble doesn't come up on the playdeb search now but it is listed in synaptic (hope I didn't miss it by one day!

I added playdeb to the repositories per the instructions on the playdeb page but when I click on the 'install now' button a launch window pops up that says 'apturl' choose an application. Not sure what to choose there so I tried just finding the games in synaptic, thats where I get the error code.

---

### Post by jtarin on 2011-01-13
[Try here.]("http://packages.ubuntu.com/lucid/i386/libsdl-image1.2/download")
Read the instructions at the top of the page.

---

### Post by thatguruguy on 2011-01-13
> **mystmaiden said:**
> Thanks for the replies, two out of three of the games I mentioned list 10.04.

Frozen Bubble doesn't come up on the playdeb search now but it is listed in synaptic (hope I didn't miss it by one day!

I added playdeb to the repositories per the instructions on the playdeb page but when I click on the 'install now' button a launch window pops up that says 'apturl' choose an application. Not sure what to choose there so I tried just finding the games in synaptic, thats where I get the error code.

Apturl is just a version of apt (the package manager) that works with urls. It is the appropriate application to use.

---

### Post by mystmaiden on 2011-01-13
Thanks again for replying. I wasn't seeing the 'send to' on the apturl popup. I need to brighten up the print. It still gives me the same error code.

I went to the page jtarin suggested and tried adding

```
deb [http://ubuntu/wikimedia.org/ubuntu](http://ubuntu/wikimedia.org/ubuntu)
```but I got an error message. Also I'm not sure how this works. It says 

```
You can download the requested file from the pool/universe/s/sdl-image1.2/ subdirectory at any of these sites
```Is there some way to download the file from that specific spot? 
So confused...

---

### Post by jtarin on 2011-01-14
> **mystmaiden said:**
> Thanks again for replying. I wasn't seeing the 'send to' on the apturl popup. I need to brighten up the print. It still gives me the same error code.

I went to the page jtarin suggested and tried adding

```
deb [http://ubuntu/wikimedia.org/ubuntu](http://ubuntu/wikimedia.org/ubuntu)
```but I got an error message. Also I'm not sure how this works. It says 

```
You can download the requested file from the pool/universe/s/sdl-image1.2/ subdirectory at any of these sites
```Is there some way to download the file from that specific spot? 
So confused...Sure just click a link and Nautilus will open wanting you to select a download folder on your computer. Just like Windows....download then right-click the file and choose "Open with Gdebi Installer" It will install.

---

### Post by mystmaiden on 2011-01-14
Jtarin, thanks for replying. I understand that a regular download off the web would work that way, but Synaptic?

---

### Post by jtarin on 2011-01-14
Open Synaptic and got to the Menu at the top "Settings>Repositories" ensure they are checked as in the attached screenshot.Then update your repositories. It should be there in Synaptic now if you search for libsdl-image.[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by mystmaiden on 2011-01-14
Thanks jtarin, sorry for the confusion, I originally thought you were talking about a command for the terminal or an address to enter in to the browser. 

I had everything checked that you showed, except that I also had 'source code' checked. Unchecked that, and updated then let sources choose the best server and ta da! There it was.

Success!! 

Thanks so much everyone!

mystmaiden

---

### Post by jtarin on 2011-01-14
> **mystmaiden said:**
> Thanks jtarin, sorry for the confusion, I originally thought you were talking about a command for the terminal or an address to enter in to the browser. 

I had everything checked that you showed, except that I also had 'source code' checked. Unchecked that, and updated then let sources choose the best server and ta da! There it was.

Success!! 

Thanks so much everyone!

mystmaidenYour welcome. You might mark this thread as solved. A helpful hint if you have upgraded to 10.04 you might want to change your version under your signature.

---

### Post by mystmaiden on 2011-01-15
Thanks for the heads up. The only way I know to mark something solved is to edit the first post - hope that's right?

and I got my version changed in user cp now :)

---


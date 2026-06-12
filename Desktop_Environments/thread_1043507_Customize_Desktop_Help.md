---
title: "Customize Desktop Help"
date: 2009-01-18
forum: Desktop Environments
---

### Post by camerongriser on 2009-01-18
Hey Everyone,

I'm extremely new to linux and just downloaded ubuntu to my laptop. I am a computer science major and i felt like everyone with my major should at least test out linux. I have seen a lot of videos and would really like to customize my desktop. I really like linux but i am having so many problems. I have downloaded emerald and compiz, but neither work. I have read forum after forum and have come to the conclusion that it has something to do with my graphics card. To give you a little more information about my system, I have a ASUS G50V laptop with a NVIDIA graphics card. I think these problems with compiz and emerald have something to do with my graphics card. If anyone could help me out that would be greatly appreciate.

FCC
Fellow.Computer.Craver

---

### Post by dkev on 2009-01-18
Make sure your using the recommended Nvidia driver (177). System/Administration/Hardware Drivers.

---

### Post by oaqster on 2009-01-18
do you know what nvidia card you have? cuz some of the cards dont work that well with the default driver.  run "lspci" in a terminal and look for your vga card.... if its not correctly listed you might need to download and install the appropriate driver from nvidia's website or you could use Envy that will detect, download and install the correct driver for you.

also goto System -> Preferences -> Apearence -> Visual Effects, and select the last option "Extra", if your card's driver is correctly installed and its good enough to handle better visual effects, this will enable some default eye candy for you like wobbly & snapping windows, minimize & maximize effects etc.

if that goes well goto System -> Administration -> Synaptic Package Manager and search for compiz, you want to search for compizconfig-settings-manager and mark that for update (and any other dependencies that come up) and hit apply.  this will give you a new item under System -> Preferences called "Advanced Desktop Effects Settings", which will give you a larger array of goodies and eye candy to enable and configure.

let me know how it goes
- oaqster

---


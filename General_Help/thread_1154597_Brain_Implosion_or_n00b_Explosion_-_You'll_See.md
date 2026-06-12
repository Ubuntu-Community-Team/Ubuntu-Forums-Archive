---
title: "Brain Implosion or n00b Explosion - You'll See"
date: 2009-05-09
forum: General Help
---

### Post by acer8930 on 2009-05-09
Ok, trying to install build-essentials which depends on g++-4.1.

g++ depends on libstdc++

however

libstdc++ depends on g++

What? Screens attached, someone please tell me what I'm missing.

(These windows were side-by-side I don't know why I split them up)

---

### Post by MaxIBoy on 2009-05-09
Just "sudo apt-get install build-essentials" in the terminal, APT will handle all the dependencies for you. No need to do it manually, you'll just screw things up. (Took me more than once before I learned my lesson: only install things manually if you **have to**. Most of the time, the version in the repos is just fine.)


If you try to install it and it complains about broken packages, run "sudo apt-get -f install." Be sure to **write down what packages it chose to remove, so you can install them later**.

---

### Post by acer8930 on 2009-05-10
Manual installation is my only option atm as I live in the country and I get no wireless and Ubuntu doesn't detect my modem so the only option I have is to download everything through Vista then reboot into Ubuntu.

I have another thread trying to get my modem working but I'm waiting for someone to reply.

Does anyone have any recommendations or am I just gonna have to go find a WiFi spot?

--EDIT--
I found a network cable lying around, so now I do have internet within Ubuntu, still Dial-up though. 
<i entered the command in the terminal to get build-essentials,  but it could not find the package, same when I searched Synapsis.

---


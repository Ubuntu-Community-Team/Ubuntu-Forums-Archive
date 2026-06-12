---
title: "opengl games are not working properly"
date: 2013-09-28
forum: Gaming &amp; Leisure
---

### Post by Ziad_Arafat on 2013-09-28
Whenever I play a game like Team Fortress 2 or Chamions of regnum or any game that uses opengl on ubuntu 13.04 (this still happened in previous ubuntu versions so forget downgrading) the graphics are all wrong. Example all the textures are gray. in TF2 everything is black exept the character it's just a hideous disaster. My drivers are updated but i also noticed something strange. My PC uses nvidia GEFORCE 310M 1GB but ubuntu details settings shows that it's actually Intel® Ironlake Mobile x86/MMX/SSE2. Is there a solution to this problem? I heard that alot of games on linux dont work with intel video cards but mine is actually Nvidia what's up with that?:confused:

specs: Memory 3.7 GiB

processor: Intel® Core™ i5 CPU M 460 @ 2.53GHz × 4 

Graphics: (ubuntu's assumption which is incorrect) Intel® Ironlake Mobile x86/MMX/SSE2
(the actual graphics card model) Nvidia GEFORCE 310M CUDA . 1GB

OS type: 32-bit

disk: (partition currently using) 380.7 GB  (full disk) 500 GB

(i have another partition with Kali linux for penetration testing) 


is there a way to update/upgrade opengl itself? could that be the problem 

btw i can upgrade to a 64 bit operating system if that helps but if it doesn't I am not ready to do it for now good reason it would mean having to reinstall both Kali and Ubuntu and it's just not very fun, but if it is the problem i am willing to do it because i was planning to do it at some point

---

### Post by Arthur_D on 2013-09-29
I guess you have a hybrid graphics solution in your laptop. I suggest researching e.g. [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics) perhaps especially [https://help.ubuntu.com/community/HybridGraphics#NVIDIA_Optimus](https://help.ubuntu.com/community/HybridGraphics#NVIDIA_Optimus) as that may be likely to apply.

---


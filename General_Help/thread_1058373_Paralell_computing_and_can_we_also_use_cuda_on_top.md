---
title: "Paralell computing? and can we also use cuda on top for encoding?"
date: 2009-02-02
forum: General Help
---

### Post by RedeyeAce on 2009-02-02
Hi All,

Did a search and couldn't find anything, so thought I'd post here to be pointed in the right direction.

Im looking to tie up several pc's which are already over a 1gb lan connection for paralell computing.

I have:-

1x Vid edit suite : vista 32bit 32ghz (dual quadcore 9775's) 4GB Ram with a quaddro card attached via 10gb Ethernet to a:-

1x San:  Windows storage server Quadcore 2.4ghz Raid 50 (soon to be a raid 5 due to overhead) array with 6TB storage using iscsi, Sata drives

1x Old Edit Suite: dual xeon 2.8's with 2GB ram and a quaddro

1x Ubuntu Server: P4 2.8 1bg Ram 8x 150gb drives  (raid not set yet) Geforce 4 MX440

1x Ubuntu desktop P4 3.2 Onboard GFX 2Gb ram,

1x Kitchen Ubuntu desktopPC P4 2.8 512Gb ram onboard

1x Laptop Windows Vista Ultimate 32bit Dualcore 2Ghz Nvidia 8600M GT

1x PS3 

Multiple other drives including 2x Netgear SC101's, I know yuk, but i needed iscsii at the time for cheap :(

1.  Can this be done
2.  Will all processes be shared across all machines
3.  Can I Throttle applications to switch processing power
4.  I have multiple Nvidia quadro / 8 series cards can I tie these in also using cuda to improve upon the paralell computing
5.  Which Video encoders would work best with this application
6. I saw an edit suite for linux many a moon ago, which i was going to try on the old edit box can anyone point me in the right direction.


I know its a lot for my first post, I'm really excited by the possibilities.  Tried linux bout 6 years ago and kept relatively in the loop, but it seems now might be the right time to try again.

I greatly appreciate any help with regard to the above and thanks folks for reading the wall of text!!

---

### Post by mb_webguy on 2009-02-03
Unfortunately, you can't simply connect some computers together and expect to run normal applications using the processing power of the entire network.  Distributed computing just doesn't work like that.

Parallel processors *on a single motherboard* can speed up software designed to take advantage of multiple processors (i.e. use multiple threads or processes).  But this isn't the same as distributed computing, which is what you're describing.  No matter how you network the computers, the connection speeds will never even come close to your internal bus speed, so even if this could work the way you want, it would actually slow things down, rather than speed things up.  Distributed computing is perfect for very large problems that can be divided into numerous small chunks, such as gene sequencing or protein folding, but not for desktop applications.

Think of it this way.  Let's say that a brain can only think one thought at a time.  You, with your one brain, are playing a game of chess.  Whenever you make a move, you have to examine each possible move one at a time, and only once you've considered all possible moves can you decide which is best.  Now, if you had several brains, and could therefore consider several possible moves at once, this would considerably decrease the time it takes you to decide on your move.  This is parallel computing, since you (the computer) have multiple brains (processors) that can consider several aspects of a simple problem.  

Now consider that instead of putting more brains in your head, you brought some friends along, and had them try to do the same thing.  For each move, you'd have to decide which friend is to consider which possible move, and communicate that to them.  Then, you'd each have to consider the assigned possible move, and each of your friends would have to communicate his expected outcome of his considered possible move to you, and only once each of your friends has finished telling you what they thought of the move they considered, can you choose which of those possible moves you want to make.  As you can see, that's a lot of discussion, and rather than speed up your chess game, it would slow it considerably.  

Now consider that instead of playing chess, you're adding all of the integers from 1 to one billion.  This can be sped up by having more brains, but only to a point, since you can only fit so many brains inside one head.  If you had two brains, for example, you could have one add all the numbers from 1 to 500 million, and the other add all of the numbers from 500 million and 1 to a billion, and the sum of those two results would be your answer.  

But if you instead had ten thousand people, and gave each of them ten thousand numbers to add, and and then assigned a few of them to add together some of those answers until you'd added all of them together, then you'd get to the result a lot faster.  It would take a lot faster for one person to add ten thousand numbers than it would to add half a billion numbers, and the sum is a very small amount of information to communicate.

So if you have a large problem that can be broken down into many, many smaller problems, then distributed computing might be what you need.  But generally these problems involve the hard sciences and the analysis of small chunks of very large sets of data.  Most people aren't trying to solve this kind of problem.  Most people are just trying to play World of Warcraft or watch a video in VLC.  These applications can be broken down into a handful of discrete parts, but there's a limit.  Parallel processors can speed these sorts of things up, but not distributed computing.

---

### Post by jespdj on 2009-02-03
The nVidia [CUDA SDK](http://www.nvidia.com/object/cuda_get.html) is available for Linux. I downloaded it and played with some of the examples.

Ofcourse you'll need an nVidia graphics card that supports CUDA (8xxx- or 9xxx-series or newer). Writing software for CUDA is not so easy - you'll need to structure your algorithm in a way that's suitable to the parallel architecture. But if you do it right, you can get speedups of up to 100x or even more compared to a normal, non-parallel CPU.

---

### Post by RedeyeAce on 2009-02-03
Heya guys,

Thanks for those replies, funnily enough I woke up this morning and was thinking just how much data would be used over the network and realised that by the time the constant handshakes were being actioned etc, that it would probably be slower for normal apps.

However if i am working on largevideo files i.e. I have to encode hours worth of 1080p footage (every month )from an almost uncompressed Quicktime source to a 1080p MPEG 2, would this benefit from the paralell computing?   Im guessing no and my current setup on the 32ghz box and quaddro card running a software encoder which uses CUDA is already the best option.

Now theres a thought, I'm now wondering whether theres any clever versions of a linux based edit suite that also render using CUDA, that would certainly speed things up.. hmmmmmm

Im no programmer tbh, I would love to be able to throw some code together but its not my bag.  Hence using my current setup the encoder already uses cuda.  If there is a nice Encoder for Ubuntu with lots of advanced setting that uses cuda I would have a look at it, to compare performance.

Cheers for the replies so far, really are most appreciated.

---

### Post by RedeyeAce on 2009-02-03
Bump&#9679;&#9679;&#9679;&#9679;&#9679;&#9679;

---


---
title: "Help! Many problems.."
date: 2005-12-11
forum: General Help
---

### Post by Torez on 2005-12-11
[B]Brief Foreword:
[/B]
Okay, first of all, lemme say that I'm a total noob at anything to do with Linux or Ubuntu. The first time I ever even saw anything to do with Linux actually operating, was last week. I've managed to master certain things, not perfectly, but enough to understand them, however, a few things are now really getting on my nerves, and no matter how long I spend on the IRC room, it never gets solved.

Second brief request/warning: So far on the IRC rooms, I ask for help, get ignored, ask again some time later, get half an answer, then I never get helped again. I understand perfectly that the IRC room is under high demand and that there aren't really enough people there to help everyone at once, but please, if you start helping me, continue to! This is unfamiliar territory for me, and all that has happened so far, is I get dragged into the Deep end of a pool I can't swim in yet, then left there!

Can I also just say, that I have my Dad's temprement. This'll mean nothing to you guys/gals, but I'm not so keen on my Dad. He's not the 'friendliest' of guys to hang around with. He loses his temper too easily. So what I'm saying is, if I start getting mad and stressy, I'm really sorry, I honestly don't mean to be so short tempered. I wish I wasn't like him in that aspect, but let's leave that one. Don't really wanna delve into my personal past now, would I? Stick to the problem in hand..

**The Problem(s):**

I've installed Ubuntu 5.10 on my server machine. I have to say that so far I'm rather impressed. It's a real breeze to set up, and I like that very muchly, but so far I'm having repeated problems, and I can't find help anywhere else, so I've come here. It could be that I'm just not searching on the help areas correctly, but I haven't found any help there, or on IRC, so I'm coming here now.

**Main problem: "Honey, I blew up the resolution.."**

The resolution on my installation is now too big for the screen. It was working fine at first, but I had to restart the box after everything froze, and when it came back, it was like this. Since then, I've formatted and reinstalled once, but this time it has stayed.

The screen seems to be about 2 times too big for my monitor, and no amount of changing the resolution helps. I've edited some xorg file as recommended in IRC to have a virtual command in it, and yet it has made no difference. The only way I can see certain parts of my screen is by moving my cursor to the edge of the screen, and then it scrolls to the sides; as if it knows full well that it's too big. Any suggestions here? It's not stopping me from using the server machine, but it's a pain in the neck, one I didn't have at first..

**Second problem: "More Wireless Woes.."**

My last server install ( Windows XP Prof. ) managed to work great with my setup. The internet comes 'in' to the server using a wired connection, but what I used to have too was a wireless connection on ad-hoc that broadcasted my internet around my house for my PDA to use freely. It worked great. Ubuntu wants nothing to do with it.

I did find a few guides, but they were incredibly sketchy, and for a newb like me, made no sense at all without screaming on IRC and ragging my hair out for many hours. The first problem was that Ubuntu detected my wireless card ( RTL8180L ) on the device manager, but in the network list and on iwconfig, nothing was there. A little ( Understatement ) messing around got it to detect my wireless card, but the next problem started. No matter what, Ubuntu was constantly reverting to my wireless card as it's default gateway, so my internet would shut down. If I tried turning it back to eth0, it would switch back again. If I disabled wlan0, it would not allow ANY of my network connections to be the gateway. I managed to fix this too, but it took editing config files I don't understand, and making Ubuntu somewhat unstable.

Basically, what I'm asking, is could someone either find me or make me a guide that tells me, from scratch, how to deal with all of these problems ( Including a decent guide on using Ndiswrapper to install my RTL8180L driver ) , and set up internet going into the server machine, then also being broadcasted on an un-encrypted wireless ad-hoc network? That'd be awesome.

**Third Problem: "Printing Problems.."**

... Kinda... this one's not so much a problem as it is a simple request for a favour. I don't understand print sharing on Ubuntu. After some messing around with Windows Drivers I got my printer ( HP-PSC 1215 All in one ) to print. Perfect. It was all great till I followed a Howto on Print sharing. Then it all went down the drain, and the server never printed again. Can someone find/make me a guide on setting up the Printer on the server machine ( Which is directly connected ) So that the two other machines in my network ( Windows Machines, both XP Pro ) can print on that printer? Cheers.

**Fourth and Final Problem: **

I'm not sure I've remembered this correctly. This post has gone on for so long I forgot this last one. If I remember correctly though, this is it:

Why is it I can't login to root? It never told me of any password thing, so what does it set the password to by default? Typing sudo before everything gets a little tedious, although it's nothing too major. If anyone could just answer this question, that'd be cool, but if not, it's fine..
[B]
Closure:[/B]

Wow. What a long post. If you read all that, you're brave. Either that, or you've nothing to do right now. Still, you're brave. Thanks for taking time to read my problems, and I really hope you can help me here. Even if you can answer or do me just one of the things I ask, that'd be a great start. If one person could do just one of the things I asked, but there are many people who can all do the different bits, then all I have to do is put all their answers together. So please, please; help me out! And remember, when you answer, please make sure you explain it how you would to someone who had never seen anything to do with Linux before - 'cos essentially, you are..

Many thanks in advance,

*Torez*

---

### Post by Ocxic on 2005-12-11
The root account is diabled by default.
type  "sudo su"  in a terminal to login as root, type exit to stop being root and return to the normal terminal.

---

### Post by mherring on 2005-12-11
I don't know how it is on IRC, but--if you want help here---you need about 10X less words.

May I suggest that you make several posts---each on a specific topic---with keywords in the title.  Challenge yourself to ask each question in 50 words or less

---

### Post by zoiks on 2005-12-11
You are giving people too much to swallow at once.  I recommend doing the following:

1) Break your problems down into the separate pieces.  Like "I can't log in to root", or "windows doesn't see my file shares", etc.
2) For each problem, search the ubuntu forums, the debian mailing lists, and of course, google, to try to find a solution.  Look long and hard because usually someone else has had and solved the same problem.
3) Assuming you haven't found a solution to a given problem, post a question that is as specific as possible.  Include copies of relevent logs or configuration files, such as /etc/samba/smb.conf or /var/log/cups/error_log.  If it's a problem with an application, try running the app from a terminal so you can see any error output.  Include information about your setup and the things you've tried so far.
4) Have patience.

Taking these steps will get you a lot further along then asking people to find or make you a user guide.

---


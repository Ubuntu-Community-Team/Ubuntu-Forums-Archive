---
title: "Help w. Remote Desktop"
date: 2009-02-17
forum: General Help
---

### Post by Ketara on 2009-02-17
I've been looking for a couple days now and have been unable to find a thread with organized instructions on how to use remote desktop, so I'm wondering if anybody could hold my hand through it.

Essentially this request came from the fact that I do all of my mothers tech support. She asks me to come to her house just to defrag her desktop because she doesn't know how to do it, and forgets every time I teach her. I don't mind doing this but I'm hoping I can set up a way to do it from home or work and remove the part where I have to run over every time something goes wrong.

However, remote desktop and its uses are pretty foreign to me, and the threads I have found on the whole do not discuss how to remote a Windows machine from Ubuntu, or give very messy instructions that I do not understand.

I'm interested in learning how to do this in other situations as well, but at the moment we're talking about using remote desktop to access a Windows XP Home desktop from an Intrepid laptop. The XP machine is connected wirelessly to a router.

Thanks!

---

### Post by mikewu on 2009-02-17
Does it actually need to be a remote desktop or could it just be a remote shell. 

You could set up a ssh server on her computer. OpenSSH provides a minimal cygwin enviroment. freeSSHDd is another option. You could just commands that way. 

If you need a remote desktop, then tightVNC will work. 

Honestly if you only need to defrag a couple times a week make a batch file to defrag it in windows and put it in their scheduler. 

defrag.bat
```
defrag c: -f 
```
//Force defrags C drive even if low free space.

And stick that Scheduled Tasks.

Method 2:

C:> at 18:00 /interactive /every:M,T,W,Th,F,S,Su "defrag c: -f"

Hope this helps!

---

### Post by Cybie257 on 2009-02-17
> **Ketara said:**
> 

I'm interested in learning how to do this in other situations as well, but at the moment we're talking about using remote desktop to access a Windows XP Home desktop from an Intrepid laptop. The XP machine is connected wirelessly to a router.

Thanks!

A few things. First, because you are using Home edition, you need to install a Remote Desktop server. Like the previous post, TightVNC was suggested. i've had luck with all VNC servers (Open Source). If the Windows computer loads right to the Desktop without a user password, stay away from UltraVNC as that requires setting up a user with password for security. I use it and love it and like the File transfer feature built into it. I'm not too familiar with TightVNC (only played with it once a long time ago).

Also, since it is hooked up to a WIFI router, you will need to forward port 5900 to your moms computer. Also, I suggest setting the PC to be remoted into, as a Static IP for the purpose of port forwarding. If you forward to say IP:192.168.1.3 and she connects another time and DHCP gives the computer IP:192.168.1.5, you won't be connecting. 

What type of Internet service do you have? Cable? DSL? Cable uses a modem, DSL uses a router. With DSL, you also need to forward the port in that as well to the WIFI Router. For Cable, I would have to get back to you. Only set up one of those with remote and it was a pain to find how. It was easy once I saw how, but can't remember now. lol

Hope this helps a bit.. I will try to keep up with this thread for more help, but have to get to class for now. Good Luck..

-Cybie

---

### Post by Ketara on 2009-02-17
It's not just defragging, that was just the silliest example I could think of. Honestly it's a half a dozen different recurring problems but when she calls me I basically get "my computer is slow come fix it." Sometimes nothing is wrong at all but I still have to check because she is my mother.

The other half of this request is, really I just want to learn how to use remote desktop because I think it's pretty cool.

If SSH would work for that, then sure that's an alternative, but I don't know how to do that either. I checked up a bit on that when I was searching and didn't find any good threads of that sort Ubuntu->Windows either.

---

### Post by Ketara on 2009-02-17
@Cybie

It's a Comcast cable connection. Modem to a Linksys router to her desktop upstairs, which has a USB wireless card. Her computer does not have a login password.

Is VNC a necessity? I've read both that VNC is amazing and that VNC is terrible. What does VNC do that the base remote desktop program doesn't?

---

### Post by Cybie257 on 2009-02-17
I wouldn't say VNC is a necessity, but probably the easiest to setup. I've been using it for about 2 years, remoting into home from work, school, and wherever else I go. As for the Remote Desktop built in to Windows XP, it's only available on the Professional version for some reason. I think I read that you can download something from MS to install it, but have never been able to confirm that.

As for the Cable modem, I'm still trying to remember what had to take place. I am looking (remotely) at my friends computer. I think I had to disable 'block WAN ping'. I'm about 97% sure that was the setting. Basically, you have to allow the outside workd to be able to ping your inside network. Your WIFI Router will become the primary security (firewall) and within that, you will want to forward the 5900 port to the intended computer to be remoted into.

In order to get your outside IP address, you can go to [www.whatismyip.com](www.whatismyip.com). Then you can try from remote to login/test your remote setup. 

Let's see how far this gets you and I'll try to keep up on this to help you out. BTW, VNC connections from a Linux to a remote computer is so much faster that from a Windows computer. :) Smoother and faster screen updates. At least from my experience. 

-Cybie

---

### Post by Ketara on 2009-02-17
Okay. I'll play around with it.

Probably will be a couple days before I have any worthwhile news though, this isn't something I'm going to get up and go do right away.

---


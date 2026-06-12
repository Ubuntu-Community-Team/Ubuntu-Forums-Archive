---
title: "Getting Synergy to Work (with asus netbook ubuntu and imac macos 10.5)"
date: 2011-06-08
forum: Desktop Environments
---

### Post by johntkucz on 2011-06-08
Getting Synergy to Work (with asus netbook ubuntu and imac macos 10.5)

If I could some how describe how frustrating this has been, I would, but other than detonating and defenstrating my imac, I don't know how to communicate how infuriating setting this up has been (I really loathe macs, can't stand their protocols, how locked down they are with software and hardware, and they merely do not interest me, but windows and especially ubuntu, does).

netbook remix on asus 1001p 
mac os 10.5 on imac

Want to have the netbook be the synergy server controlling the imac as client.

I've read numerous tutorials and how-tos but ran into obstacles with each.

This one was the most helpful.

But I installed xcode (a rubbish wayward solution and think that this may be too old of a version so now I have multiple versiosn and multiple mysynergy.conf files) and it didn't build with an SDK error.

I tried other tutorials.  I have SynergyKMV in imac control panel but but I also may have aold version of synergy and qsynergy.  Confused on which versions of synergy.  I've been at this off and on for over a year :(

On netbook_remix netbook 1001p I've got Quick synergy.

hostname for imac is crpimac.local
hostname for netbook is netbookbu

[http://www.drquincy.com/blog/how-to-set-up-synergy-on-mac-os-x-and-ubuntu/](http://www.drquincy.com/blog/how-to-set-up-synergy-on-mac-os-x-and-ubuntu/)

was MASSIVeLY helpful with the 
hostname
ifconfig

cli commands. I abhorred guides that didn't show those.  I'll probalby make my own synergy guide after setting this up.

I'm determined to get this to work and would genuinely appreciate anyone's help with this.  




-----
When I try running netbook as client (the opposite of what I want to do but am trying to get it connected in any way possible at first) it says connection refused.

on the imac control panel it says netbookbu is not on the 'map', but it's obviously picking it up.

I'm not sure if that link I listed is for an older version of synergy.  I did the mysynergy.conf file EXACTLY as described in that tutorial (the one with the helfpul cli hostname and ifconfig learning.  I really want to amp my cli learning big-time :D)  

Getting this set up would massively increase productivity and am very determined (but simultaneously frustrated) at getting this going.


Trying to think of more information...
with infconfig
there were two ip addresses on inet
127.00001 something with mask
and and a 192 one.  I used the 192 one.

---

### Post by johntkucz on 2011-06-08
When I try to run netbook ubuntu as server with synnb.conf as configuration 

I get 


```
cannot listen for clients: cannot bind address: Address already in use

```


my synnb.conf is 
```

section: screens
	netbookubu:
	crpimac.local:
end

section: links
	netbookubu:
		right = crpimac.local
	crpimac.local:
		left = netbookubu
end

section: aliases
	netbookubu:
		192.168.1.138
	crpimac.local:
		192.168.1.30
end
```


I much MUCH more greatly prefer using CLI to set this up, but alas, still don't know what that error means and it's not working.

---

### Post by johntkucz on 2011-06-11
2011-06-11T11:50:43 FATAL: Init failed: Access is denied.


Try `synergys.exe --help' for more information.
	..\lib\synergy\CApp.cpp,275


is the error I get when trying to run synergy in window and installing it as windows service (trying to get it running in any operating system for now).

---


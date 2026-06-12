---
title: "Emerald issue that I haven't seen before."
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by highgeere on 2007-04-24
Hey everybody, I am having a problem with the Emerald window decorator for Beryl. I have been reading up on this for a while, but was only just able to actually get Beryl working on my x1600 when 7.04 was released. My problem is that title bars and window borders are broken when using emerald. Other people have had a similar problem, but I don't believe this is the same. I have attached a screenshot so you can get an idea of what I am talking about. The borders are only broken on windows, not on tooltips or dropdown menus, and the close, minimize, maximize buttons still work even though you can't see them. And the corners are still there. which is why I say they are 'broken' instead of 'not working'. I can paste my xorg.conf if necessary, but, like I said, I don't think it is a configuration issue. Thanks.

highgeere

---

### Post by MagicBytes on 2007-04-24
Hello, I just installed Ubuntu V7.04 and I also had ago at installing the 3D desktop, I am a beginner and I am too having the same issue, I noticed in the emerald-themes that the beryl theme was missing the graphic, so I suspect maybe an issue here, but personally I think it is just opacity  setting, from what I can see in Beryl management, it looks to have many many configuration settings, so I believe some where in there is an opacity adjustment because the title bar looks to be transparent, so If you manage to find this setting before I do, I would appreciate a reply please, but I will keep looking and experimenting until I find it,  I will let you know if I happen to fix it.

Other than that every things seems to work fine, mind you I had to reformat 4 times before I got it working and a few choice words thrown in for good measure... heheheheheh

Cheers MagicBytes 

:lolflag:

---

### Post by kbzona on 2007-04-24
mmm... are you using Compiz for the effects???

Try choosing a diferent Windows Decorator in beryl icon menu...

---

### Post by MagicBytes on 2007-04-24
Ok I found how to make your [COLOR="Blue"]title bar re-appear[/COLOR]...

[COLOR="SeaGreen"]Follow these steps[/COLOR]

1. Click [COLOR="Sienna"]Applications[/COLOR]

2. Goto [COLOR="Sienna"]System Tools[/COLOR], then select [COLOR="Sienna"]Beryl Manager.[/COLOR]

3. Then choose  [COLOR="Sienna"]Select Window Decorator [/COLOR]then bullet, [COLOR="Sienna"]GTK Window Decorator.[/COLOR]

You should now have your title bar re-appear again, if not log out and back in again or try a restart.

Hope this fixes you as it did fix mine..

If none of the above works for you, then let me know. (post a reply here)

Cheers MagicBytes

:popcorn:

---

### Post by highgeere on 2007-04-26
Thanks MagicBytes. I actually figured out how to change back to GTK after playing with the beryl settings. Still, though, I would like to be able to use Emerald themes as well. I don't suppose you know what the cause of the missing titlebars is?

highgeere

---

### Post by MagicBytes on 2007-04-27
Hello again, well I am thinking it is a bug, because when I try out different emerald_themes I don't see any changes, but I am searching the forums and Google for a solution and if I find a fix I will let you know.

I am lost too as to why, but they did mention that Beryl is buggy and too expect problems.

If and when they fix the bugs Beryl and the 3D desktop will be a great feature that many will pursue, the concept is a great idea and very helpful for the end user, but we have to wait until they sort things out.

I am going to really love it when it is fixed.

Sorry I can't be of any more help, but I will keep on looking for a solution and let you know.

Cheers MagicBytes :popcorn:

---

### Post by highgeere on 2007-04-28
Thanks Magic. I kind of thought you might say that. I actually found the same bug over on Beryl's forums with no resolution as of yet. It isn't the only weird issue I'm having with Beryl, but I also had to use half a dozen how-tos and still ended up needing to write my own script to run on startup. I've got and ATI X1600 card and a 64-bit AMD X2, so I'm pretty much making this as difficult as possible for myself. And really, who cares about window decorations or cube opacity when you have wobbly windows... :)

highgeere

---

### Post by MagicBytes on 2007-04-29
Hello Again, well I too have a ATI Radeon X1600 graphics card with 512 MB video memory plugged into an PCI-Express Slot, I have 1GB ram, an AMD Athlon 3200+ CPU and a Gigabyte GA-K8N-SLI mother board, I have tried reformating and reinstalling and then tried the same web sites instructions and still the same old thing, I think there is some thing missing because I pyshiically have to install the Beryl manager from the synaptics package manager to see the Beryl themes on the task bar, but I keep trying different things untill I get it working properly, I am sure there is something missing from the instructions that I am going by.

Below is the web sites instructions that I am following on how to install the 3D desktop and Beryl plus the emerald themes manager.

[http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

I don't know which intructions you are using, maybe between the two of us we get some thing officially working.

Well I keep you posted on my progress...

Cheers MagicBytes :popcorn:

---

### Post by mctt on 2007-06-29
Hello highgeere,
I found pretty much the same thing on 64-bit AMD X2 (Inspiron 1501). I hope a fix comes out but for now wobbly window are a bit of fun.

---

### Post by andrewsomething on 2007-06-29
@ highgeere  

I stumbled across that issue before. It seemed to have some thing to do with having incompatible versions of emerald and Beryl. I was getting the two programs from different repos. Are you getting them from the same repo? If you don't know, run the following commands in the terminal to see what versions you have and where they come from. Post your results if you don't understand. 

apt-cache policy emerald

apt-cache policy beryl

This is what the results refer to:

```
package-name:
  Installed: <installed-version>
  Candidate: <version-installed-when-doing-apt-get-upgrade>
  Package-Pin: <version-of-Pin-in-etc-apt-preferences>
  Version table:
 *** <some-version> <minimum-priority-to-consider>
       <priority-of-this-instance> <repository1>
       <priority-of-this-instance> <repository2>
 *** <some-other-version> <minimum-priority-to-consider>
       <priority-of-this-instance> <repository3>
       <priority-of-this-instance> <repository4> 
```

I'm not running 64bit, but might be able to help. Hopefully this might at least put you in the right direction.

---


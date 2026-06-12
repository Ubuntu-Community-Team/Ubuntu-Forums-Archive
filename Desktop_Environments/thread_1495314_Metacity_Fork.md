---
title: "Metacity Fork"
date: 2010-05-27
forum: Desktop Environments
---

### Post by screennameless on 2010-05-27
I'm considering forking Metacity, or even the current GNOME project into something new.

I don't like where Gnome is headed with the Gnome Shell. It lacks customization, is rejecting Compiz, etc. and seems to be an overall huge step backwards for Gnome. Now, some people may not like desktop animations, but I, for one, enjoy having something to make my OS something of a "fun" OS instead of just a workstation.

So anyway, what I'm thinking of doing is: forking the project just before Gnome Shell is integrated into it, and starting it myself. (With help from the community.)

My goal here is total user control. I want users to have the option to run Compiz if they so wish, or to customize the UI anyway they want it. Or even to run Gnome Shell if they so wish.

Any thoughts?


~~UPDATE~~
I would also consider doing a rewrite of Gnome Shell depending on how it is once it's released.

---

### Post by Seaniesean on 2010-09-28
Well, I'd be really delighted if you'd fork metacity/gnome after the release of gnome shell.  If you're still there, that is...

Surprised no one else thinks it's a good idea..?

---

### Post by screennameless on 2010-09-28
Well, I'm still considering it. It's a big project though, so I could never do it alone. 

However, from what I've heard; GNOME is planning on adding the option to switch back to the default user interface? I'm assuming this means they're no longer planning on forcing users to use the shell.

I suppose what I do will depend on what happens after the 3.0 release.

---

### Post by 3Miro on 2010-09-28
I have been thinking about something like that myself. The issue is that there already are alternatives in the face of XFCE and LXDE. I think an effort will be far more meaningful in improving those two than in forking Gnome.

Metacity is too outdated to be really useful, Openbox, xfwm4 and compiz are way better. XFCE and LXDE panels lack some features of Gnome panel and there is a number of smaller features that could use some polishing (like different keyboard layouts), but overall we have two almost perfect alternatives to Gnome-shell that are already mostly compatible with everything Gnome due to the GTK technology (here I am ignoring the QT based KDE).

---

### Post by screennameless on 2010-09-28
T'is true. Metacity is outdated. I guess more or less, the idea was forking the current gnome project in it's entirety. Who knows? Maybe by default implementing a different window manager and scrapping metacity.

I use Compiz, personally. And in my opinion, it works best with the current gnome. But since gnome is considering stopping support...

XFCE is a close second. But it still lacks the features I like from gnome.

---

### Post by moore.bryan on 2010-09-28
> **screennameless said:**
> However, from what I've heard; GNOME is planning on adding the option to switch back to the default user interface? I'm assuming this means they're no longer planning on forcing users to use the shell.
GNOME Shell was never going to be forced on anyone; always choices...
[http://live.gnome.org/GNOME3Myths#GNOME_won.27t_support_the_current_panel_and_window_manager_anymore]("http://live.gnome.org/GNOME3Myths#GNOME_won.27t_support_the_current_panel_and_window_manager_anymore")

---

### Post by 3Miro on 2010-09-28
I had good experience with Openbox and Gnome, it was very stable thought windows decorations looked out of place. Gnome should have gone for a WM like kwin, that can do no effects (like default Metacity), some effects (like xfwm) and full 3D like compiz. Now Gnome-shell is 3D only and I for one cannot figure how to use it with any efficiency. I want to give them the benefit of the doubt, maybe I haven't figured it out yet, but the best I got was using Gnome-shell + Docky (but still nowhere near what I wanted).

My opinion is that poring good tools/features from Gnome to XFCE and/or LXDE will be a more productive effort than a full fork.

---

### Post by moore.bryan on 2010-09-29
> **3Miro said:**
> Now Gnome-shell is 3D only and I for one cannot figure how to use it with any efficiency. I want to give them the benefit of the doubt, maybe I haven't figured it out yet, but the best I got was using Gnome-shell + Docky (but still nowhere near what I wanted).
I don't want to start a defense of GNOME Shell and this **isn't** trolling, but as a user and supporter of GS, I'm interested in finding-out exactly what issues you've been having and why you feel the need to use something like Docky.

Thanks!

---

### Post by 3Miro on 2010-09-29
> **moore.bryan said:**
> I don't want to start a defense of GNOME Shell and this **isn't** trolling, but as a user and supporter of GS, I'm interested in finding-out exactly what issues you've been having and why you feel the need to use something like Docky.

Thanks!

I actually want ask a few questions to someone who knows GS.

For my needs, a computer has three modes of operation: Coding with two hands on the keyboard, heavy surfing with one hand on the keyboard and one hand on the mouse and taking it easy with one hand on the mouse and one hand holding a beer. In all of those cases, I should be able to open/close windows, switch between open windows and change workspaces with minimal movement/typing.

Metaicty was the only WM that could not change desktops with a middle-button scroll, now GS is the second. In Matacity one could at leas use the panel applet to scroll over it (which is unnecessary movement of the mouse), however, in GS to change workspaces, one has to use either the keyboard or the zoom out/scroll to the right workspace/zoom in.

GS has no panel, therefore, if I have several windows open on a workspace, I have to either make sure they don't overlap (which is an interesting math problem, but gets frustrating after awhile) or use Alt-Tab (another hand) or zoom out/in (takes time). I also easily lose track of the the things that I have opened). Docky/Awn/Gnome-panel can do that with a single click.

To open a new app, one has to zoom out, pick from a list, put on a workspace, zoom in. In every other DE, one can put a number of shortcut launchers on a panel and launch them with a single click, GS doesn't have that feature, in fact all that it has is a rather empty top panel (OK this can be easily fixed with more features later on).

The zoom animation is impressive (though not as impressive as the cube or compiz in general), and after you enjoy it a few times you want to devote to more productive things. Not all of us have machines that can handle the zoom on many workspaces/windows and even if we can, it takes time to zoom which takes a toll on productivity. I would like to think that in introducing so many dramatically different features and scrapping so many of the classic ones (like taskbar and menu), the GS developers have simply figured out some new and greatly improved way to work on your computer, but I just don't see it.

---

### Post by screennameless on 2010-09-29
> **3Miro said:**
> 
My opinion is that poring good tools/features from Gnome to XFCE and/or LXDE will be a more productive effort than a full fork.

Good point. If we could port all the best features from gnome to xfce, it would be much easier and **much** easier to maintain.

> I'm interested in finding-out exactly what issues you've been having and why you feel the need to use something like Docky.

Personally, I just dislike the general UI of GS. I find it counterproductive, and rather closed -- even though it's open source.

I mean, it increases drastically the number of clicks to go from one application to another, and closes out Compiz alltogether. Now, many people say "Oh, I don't need animations, they just waste time." Well, I disagree. Sure, overall, they're useless. But it adds greatly to the aesthetics/appeal of the desktop. As I said earlier, I'd really like to have a fun, appealing OS instead of _just_ a workstation.

Yes, GS has some animations, but let's face it; they're not that great. And animations are one of the things that drew people to Ubuntu in the first place. It *looked* good. Now with GS, people are going to have to relearn the desktop. Many people who aren't that tech-savvy are probably going to drop GNOME, Ubuntu, or Linux altogether. Does that look good for us? No.

Also, the issue with graphics cards. If you don't have 3D acceleration on your card, you're screwed. No "low-graphics" mode, you CANNOT use GS anymore. You'll be dropped to a command shell, which'll confuse many people.

And finally, there is absolutely NO customization unless you want to spend a lot of time coding to get what you want. Sure, they're adding themes. But really, big deal. I like the current GNOME because it allows me to pretty much do what I want with it. And it gives me the OPTION to run GS if I want too, not forces me to.

I mean, I'm sure GS is a good idea, "reinvent the desktop", but it's just not working for me.

---

### Post by 3Miro on 2010-09-29
I would like to look at this at perspective. When KDE 4.0 came out, kwin could do barely anything, yet in a few follow up releases, it got more and more animations and "eye candy". More animations can be added to GS later. What I like about both Kwin and Compiz is that they can go with only a few basic functionality features, to full blown fireworks of effects. GS may eventually get there, however, there are some basic functionality features that I don't see coming unless someone reinvents the reinvention.

---

### Post by moore.bryan on 2010-09-30
> **3Miro said:**
> I actually want ask a few questions to someone who knows GS.I guess I have to throw-up a disclaimer that I am not a GS developer, so I might get some of these wrong! ;-)

> **3Miro]For my needs, a computer has three modes of operation: Coding with two hands on the keyboard, heavy surfing with one hand on the keyboard and one hand on the mouse and taking it easy with one hand on the mouse and one hand holding a beer. In all of those cases, I should be able to open/close windows, switch between open windows and change workspaces with minimal movement/typing.[/quote]
You can do all those things in GS said:**
> Metaicty was the only WM that could not change desktops with a middle-button scroll, now GS is the second. In Matacity one could at leas use the panel applet to scroll over it (which is unnecessary movement of the mouse), however, in GS to change workspaces, one has to use either the keyboard or the zoom out/scroll to the right workspace/zoom in.
In some of the discussion threads I've read about GS development, this wasn't a "deal breaker" for changing windows/workspaces. I never used this function in the past and, frankly, didn't even know it was a function until I read your post here. I'm not sure how many people rely on this feature. That is not to say *no one* uses it because, clearly, some do; developers just can't make everything work for everyone all the time.

[quote=3Miro]GS has no panel, therefore, if I have several windows open on a workspace, I have to either make sure they don't overlap (which is an interesting math problem, but gets frustrating after awhile) or use Alt-Tab (another hand) or zoom out/in (takes time). I also easily lose track of the the things that I have opened). Docky/Awn/Gnome-panel can do that with a single click.[/quote]
It's panel is at the very top of the screen, but you're correct: it does not contain a list of open windows. In your first scenarios (keyboard, keyboard+mouse, mouse+beer), my solutions would be, repectfully, "Windows" key for the first two (which shows the overview instead of moving the mouse to the Activities corner) and actually just moving the mouse to the Activities corner. I don't actually see that as taking much time, but that's just my take.

[quote=3Miro]To open a new app, one has to zoom out, pick from a list, put on a workspace, zoom in. In every other DE, one can put a number of shortcut launchers on a panel and launch them with a single click, GS doesn't have that feature, in fact all that it has is a rather empty top panel (OK this can be easily fixed with more features later on).[/quote]
One can also set-up keyboard shortcuts and/or put those most used applications in the "favorites" of GS, so when you zoom-out, they're listed right there for you to click-on or select via keyboard.

[quote=3Miro]The zoom animation is impressive (though not as impressive as the cube or compiz in general), and after you enjoy it a few times you want to devote to more productive things. Not all of us have machines that can handle the zoom on many workspaces/windows and even if we can, it takes time to zoom which takes a toll on productivity. I would like to think that in introducing so many dramatically different features and scrapping so many of the classic ones (like taskbar and menu), the GS developers have simply figured out some new and greatly improved way to work on your computer, but I just don't see it.[/QUOTE]
Most people I've corresponded with all really like the cube or other Compiz "candy," but understand most aren't productivity-based. If the debate is productivity versus eye candy, I will not deny Compiz/Kwin wins; however, I'm not convinced that's the debate. When I first migrated to Ubuntu, I wanted the bells-and-whistles, but my computer at the time could barely handle a straight Debian+XFCE install. When I graduated to a better system, I was a Compiz die-hard. Everything possible was turned-on and I would show-off the desktop to convince everyone to switch to Ubuntu. Now, I want a desktop that's responsive, clean, and allows me to quickly perform those "productivity" activities I need; GS is the *first* environment that does all three things for me. For a while, GS was broken in the repos and the PPA and wouldn't build from scratch for me. During that time, I went back to Metacity+Compiz and even played with the Ubuntu Netbook Edition. It was hell. Now, GS compiled a bit ago with no issues and I have it back. I can honestly say I may never again go back to any other setup.

I hope this kind of gave you some insight for a GNOME Shell advocate and user. I have no problem responding to more questions about GS... just ask!

---

### Post by 3Miro on 2010-09-30
I am very tired today, so I hope I make sense.

The beer is only one example, you can replace that with greasy chips or a number of other things. I was aware of all the things that you said, I know how I can change windows/workspaces with mouse+zoom, the thing is that this is slow. What I can currently do with a move + click under GS takes several moves + clicks. I was hoping you can give me an insight about a shortcut or something.

The mouse scroll is set by default on Openbox (LXDE and pure) as well as many distro's KDE. I think only XFCE had to be activated with a check-box (maybe distro dependent). I read many posts asking how to do that under Metacity, a number of people have requested it as well and I think one version of Ubuntu had it implemented on top of regular Metacity. I is not a "deal breaker", but it is important for a number of people, it is a small thing and it is the fasted way that I know of to change workspaces.

I am not worried about GS having too few effects, I hope I did not leave wrong impression. More effects will surely be implemented in GS 3.1 and 3.2 and so on. My issue is that the zoom effect is the only option for too many things. Furthermore, zoom is still an effect and will require certain level of hardware that will disqualify some people. I am having trouble running too many effects with Compiz on my laptop and I have left them to the very minimum (I also have a powerful desktop so don't feel sorry for me, it is just that the laptop will probably have hard time with GS). Could your old computer run GS?

While some things, such as extra effects and even mouse scroll, can be easily added to GS 3.something, there are features such as some panel equivalent that looks like will be ignored for quite some time.

The interesting thing is that in the case of two hands on the keyboard, GS is as good as any other WM/DE (which is about as good as it takes) and I am wondering if this is simply because all the developers are heavy coders. Maybe I should go and troll a little on the GS development forum.

---

### Post by moore.bryan on 2010-10-01
> **3Miro said:**
> The beer is only one example, you can replace that with greasy chips or a number of other things.
I'll stick with beer! :-)

> **3Miro]I was aware of all the things that you said, I know how I can change windows/workspaces with mouse+zoom, the thing is that this is slow. What I can currently do with a move + click under GS takes several moves + clicks. I was hoping you can give me an insight about a shortcut or something.[/quote]
A mouse shortcut? AFAIK, there isn't one for GS. I do spend most of my time with both hands on the keyboard, so a mouse shortcut would be completely useless to me.

[quote=3Miro]The mouse scroll is set by default on Openbox (LXDE and pure) as well as many distro's KDE. I think only XFCE had to be activated with a check-box (maybe distro dependent). I read many posts asking how to do that under Metacity, a number of people have requested it as well and I think one version of Ubuntu had it implemented on top of regular Metacity. I is not a "deal breaker", but it is important for a number of people, it is a small thing and it is the fasted way that I know of to change workspaces.[/quote]
Really? I used Openbox for over three years and never knew that! Hmm...

[quote=3Miro]I am not worried about GS having too few effects, I hope I did not leave wrong impression. More effects will surely be implemented in GS 3.1 and 3.2 and so on. My issue is that the zoom effect is the only option for too many things. Furthermore, zoom is still an effect and will require certain level of hardware that will disqualify some people. I am having trouble running too many effects with Compiz on my laptop and I have left them to the very minimum (I also have a powerful desktop so don't feel sorry for me, it is just that the laptop will probably have hard time with GS). Could your old computer run GS?[/quote]
Although I've never seen any "minimum specs" for GS as far as eye-candy, it's really relatively low-resource said:**
> While some things, such as extra effects and even mouse scroll, can be easily added to GS 3.something, there are features such as some panel equivalent that looks like will be ignored for quite some time.
I agree completely.

[quote=3Miro]The interesting thing is that in the case of two hands on the keyboard, GS is as good as any other WM/DE (which is about as good as it takes) and I am wondering if this is simply because all the developers are heavy coders. Maybe I should go and troll a little on the GS development forum.[/QUOTE]
That's quite possible. Like I wrote earlier, I usually have both hands on the keyboard, so it may be that GS fits my using better than someone who uses it in combination with a mouse.

I can't deny GS took some time to become accustomed to; however, I would *never* go back to anything else now I've seen it at its best (and worst).

---


---
title: "Old workspace switcher on unity?"
date: 2011-05-02
forum: Desktop Environments
---

### Post by beejee on 2011-05-02
Hi,

I've been using Natty(unity as desktop) since the beta now and it is really growing on me except for the workspaces. Is there a way to see what workspace I am on?
 
*When typing I usually switch with ctrl-alt-"left/right/up/down" but after some work i don't always know what desktop i am one so switching is usually trial and error jumping from desktop to desktop or pressing super-s to get an overview. Seeing which desktop I'm on (maybe in the unity workspace button) would help with that.
*When just using the mouse I used to click on the workspace launcher and I would be on the desktop of my choice in one click but now I need to click on the switcher, identify where I am and where I need to go and it breaks the flow of fast switching, its no advantage anymore compared to just opening all programs on 1 workspace and using super-w

I guess there are upcoming changes on the switcher as unity is still in its infancy so is there a way to put the old switcher in the top panel again?


Thanks a lot! :guitar:

---

### Post by werewolves on 2011-05-02
Personally, the first thing I do to Ubuntu (even Gnome) is set up shortcut keys to switch to a particular desktop.  I use CTRL+F1 through CTRL+F4, but whatever works.

I also use Super+S to open my switcher and then just mouse to the one I want.

Hope that helps.

---

### Post by beejee on 2011-05-02
Thanks, thats sounds like a simple and effective way so I think for the time being I'll try that! It's probably best combined with a role for each desktop so I just have to hit the shortcut that I know holds the program I want. I usually started out in one of the middle workspaces and placed less used windows on the spaces left and right.

Still, if anyone knows for a way to visualize my workspaces and contained windows I'd be happy deluxe :)

---

### Post by Krytarik on 2011-05-02
With "Indicator-Workspaces" from this guide you can at least quickly see where you are, but if you want to use it for the actual switching you would have to do two clicks, instead of one like before:
[http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/](http://www.omgubuntu.co.uk/2011/01/the-omg-guide-to-must-have-indicator-applets/)

Personally, I use Compiz' "Desktop Wall" to switch workspaces by using Edge+Click. The built-in bindings are quite sufficient for me because my workspace setup is just 2x2, but you can also set up custom commands in "Commands" and assign them to the corners.

These are the commands I was using just until recently, obviously you need the package "wmctrl" for them, my screen resolution is 1152x864, you will get the point:
```

[commands]
as_command3 = wmctrl -o 0,0
as_command4 = wmctrl -o 1152,0
as_command5 = wmctrl -o 0,864
as_command6 = wmctrl -o 1152,864
as_run_command3_button = <LeftEdge><TopEdge>Button1
as_run_command4_button = <RightEdge>Button1
as_run_command5_button = <BottomEdge><BottomLeftEdge>Button1
as_run_command6_button = <BottomRightEdge>Button1
```

---

### Post by beejee on 2011-05-02
Superb, I think I'll combine the indicator with shortcuts to each workspace.
Thanks for the help!

---

### Post by frankob on 2011-05-04
@Krytarik:
I was using the edge+click bindings in Desktop Wall, but since Natty, it just doesn't work anymore... How did you get that to work in Natty?

---

### Post by Krytarik on 2011-05-04
> **frankob said:**
> @Krytarik:
I was using the edge+click bindings in Desktop Wall, but since Natty, it just doesn't work anymore... How did you get that to work in Natty?
I'm aware that there is a bug in Natty regarding the edge bindings, if used without a button, but Edge+Click should work:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/754948](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/754948)

Since I'm not running Natty, maybe *beejee* can help.

---

### Post by frankob on 2011-05-06
In my case, it's exactly the opposite. :-/ No button edge flipping works just fine, but edge+click doesn't work... I like to use it with a click, to prevent accidental flipping.

Actually, no binding involving edge+click in Compiz doesn't work at all on my Natty installation... while just-edge works fine in every plugin.

But we are going off-topic now...

---

### Post by Krytarik on 2011-05-07
I just found another bug report that applies to your issue:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/761616](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/761616)

---

### Post by frankob on 2011-05-07
Thank you! I have subrscribed to that.
I guess all the bugs are because they gave us an unstable version of Compiz in Natty... A bad move, if you ask me.

---

### Post by Krytarik on 2011-05-07
> **frankob said:**
> 
I guess all the bugs are because they gave us an unstable version of Compiz in Natty... A bad move, if you ask me.
That implies that they had another choice, which isn't the case, imo. Development is an ongoing process, you can't expect only stable versions of every app in a rolling release, which is the case with Natty 11.04.

Greetings.

---

### Post by frankob on 2011-05-07
Yeah... but Ubuntu is not really a rolling release distro... [http://en.wikipedia.org/wiki/Rolling_release](http://en.wikipedia.org/wiki/Rolling_release)

I am not expecting of Ubuntu the stability od the Debian stable branch, but they put out a release they call stable, with its default WM in an unstable version... Maybe you are right, but then again, they should have at least warned us that standard Natty will be a release NOT adviced for every day use, if that's the case. I mean, I have been using Ubuntu for years now, they have never done something like this before.

And talking about choices, why do you think they didn't have any other choice? Gnome 2 is still in use by many, a few months more of it wouldn't kill anybody, and then there is Gnome 3... And after all, would the world really fall apart if one Ubuntu release would be published a month or two later? It already happened with 6.06, after all...

Well, I hope everything will be better in time. It's not that bad even now. It just seems to me that the whole Unity/Natty thing was rushed too much.

---

### Post by Krytarik on 2011-05-08
Ok, I didn't check before if the wording represents the facts adequately, I just saw it mentioned in the forums quite often regarding the non-LTS releases.

The point is, if you want to have only the most stable versions of included apps, you should only install LTS versions. As I said, development is an ongoing process, and since distributors and app providers are generally trying to stick with their announced release dates, you might get some not that stable apps into a 6-monthly release. Maverick had/has a lot of bugs, too, and not a few users were calling those the most buggy release ever. But now that Natty is out, a lot of users are stating that they want to go back to Maverick. Because it's that more stable? Seriously.

So, if you want all the latest versions of apps, you have to accept that not everything will run as stable as with well tested versions.

Btw., I hear a lot of users saying that Natty is the best release they have ever run, regarding the upgrade process as well as the overall performance. Of course, that also depends very much on which session option one is running . Also, what bugs one user doesn't necessarily bug every other user as well. So, the overall judgement if a release successful or not is of course fairly sujective.

---

### Post by frankob on 2011-05-08
I mostly agree with you. My only really negative criticism goes for the rush they made in publishing Unity, which at this moment, runs on a version of Compiz that the Compiz team itself is not recommending for every-day use. Of course, development is a process, there is no question about it. But what does it mean in practice, referring to Ubuntu? I don't thing that the final, non-LTS releases of Ubuntu are meant as testing platforms. But I could be wrong about that. From a Debian point of view, I more than certainly am. But, keeping a Debian point of view, Compiz 0.9.4 is not even a testing piece of software, but something in active development. On the other hand, the Ubuntu website doesn't say anything about Natty being unstable. On the contrary, it is almost incouraging the occasional passer by to download and install Natty rather than Lucid. One would conclude that, all right, it is not an LTS, but it should include stable releases of various software inside. Which is true for all packages, except Compiz, the default WM... I am just seeng it as an inconsistence.

You are right, if one wants the most stable software, there are the LTS releases. On the other side, if one wants to test and/or develop new software, there are alpha and beta releases, not finals.

---

### Post by Krytarik on 2011-05-08
> **frankob said:**
> but it should include stable releases of various software inside. Which is true for all packages, except Compiz, the default WM... I am just seeng it as an inconsistence.
Unfortunately, that is not true, at least the theme reverting bug is still around to some extent, and, more seriously, 'gnome-screensaver' seems even more unstable than in previous releases, which effectively means that a considerable number of users are not able to get their systems out of screensaver mode and/or locked state. So, that makes it more consistent. ;-)

---

### Post by frankob on 2011-05-09
hm... I have never experienced any screensaver issue in Ubuntu whatsoever, not on my machines, nor on my frends' machines... But I am aware that Ubuntu is bound to act in strange ways sometimes, and there is no reason not to believe you.

So, I see, THAT is the kind of OS they are trying achieve. I guess the unstabilities are a way to make it more familiar to Windows users. ;-)

---

### Post by gweaver on 2011-05-20
> **frankob said:**
> I mostly agree with you. My only really negative criticism goes for the rush they made in publishing Unity, which at this moment, runs on a version of Compiz that the Compiz team itself is not recommending for every-day use. Of course, development is a process, there is no question about it. But what does it mean in practice, referring to Ubuntu? I don't thing that the final, non-LTS releases of Ubuntu are meant as testing platforms. But I could be wrong about that. From a Debian point of view, I more than certainly am. But, keeping a Debian point of view, Compiz 0.9.4 is not even a testing piece of software, but something in active development.

I've been put off upgrading to 11.04 because of problems with Compiz. I don't like Unity, so I thought I'd use the classic desktop with Compiz instead. Unfortunately Compiz doesn't load automatically, the windows are sometimes drawn without the menubars, and the edge button functionality (for expo etc.) doesn't work. Apparently the last bug (and probably some of the others too) is known for the unstable version of Compiz. The last stable version was 0.8.6, but presumably Canonical needed functionality in the newer version for Unity? If not, I can't see what their excuse is. Hopefully they'll backport the next stable release of Compiz to 11.04.

---

### Post by Krytarik on 2011-05-20
> **gweaver said:**
> Unfortunately Compiz doesn't load automatically
Please see this guide on how to see the result of the Compiz support check, and, if needed, how to skip that upon login:
[http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://ubuntu4beginners.blogspot.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)
> **gweaver said:**
> but presumably Canonical needed functionality in the newer version for Unity?
I really think so, yes.

---

### Post by Copper Bezel on 2011-05-20
Listening to Shuttleworth's last keynote, everything was focused on 12.04. I get the nasty feeling that 11.04 really is more bleeding edge than other releases, and that it *is* more like beta testing than other non-LTS releases have been, with the goal of getting Compiz, Unity, and Gnome 3 stable by the time 12.04 rolls around. I don't know how else that could have been handled, since 11.04 introduced Unity and 11.10 introduces Gnome 3, both of which are going to need a fair bit of testing.

But yes, it *is* subjective, since stability on one piece of hardware or regarding one set of features may not be stability for another.

---


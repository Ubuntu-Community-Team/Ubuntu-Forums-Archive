---
title: "Combine Gnome shell and Gnome classic features"
date: 2012-06-26
forum: Desktop Environments
---

### Post by mojo2012 on 2012-06-26
Hi guys,

I tried many deskop environments ... unity, gnome shell, gnome classic, cinnamon. And all of them have some pieces I would like to use but some other annoyances that make me crazy.

These are my must-haves:
* Panel at the top: global menu that is always visible, all indicators on the right side
* hot corner for invoking an overview, this overview has to allow to switch to workspaces, drag applications and windows to different workspaces/screens.
* Dock at the bottom or left to start favorite apps
* Use a unity dash approach for launching other apps

With Unity the global menu is not visible by default, but it has a good launcher, window management is buggy and not intuitive. 
Why can't i combine Comiz Scale and Expo? It would make live so much easier.
I like the Gnome shell approach regarding window management better.

Gnome shell on the other hand lacks a global menu, at least a useful one. I don't want the menus be hidden in submenus and so on.

Additionally Gnome shell overview shows the workspace switcher only on one of my screens (dual screen setup? Why?
Additionally I'd like to have horizontal workspaces and the switcher should be either on top or on the bottom of the screens.
Furthermore some status icons are on top and some are on the bottom?!

Gnome classic allows me to configure the top panel as I like it. But the window management is the same as in Unity ... crap. Scale and Expo are not combinable here too.

Cinnamon on the other hand has a very windows vista-y approach. I don't like the start menu and the overview mode looks very unprofessional. Also not global menubar

So my idea was to combine the best parts of these DEs
* Take the launcher from Unity
* Use Gnome Classic's panel with global appmenu and indicators
* Take Gnome Shell's overview mode (invoke with hot corner or button in the gnome panel)

Unfortunately gnome-panel doesn't start up when gnome shell is running. The DEs seem to lock each other out - which makes sense ...

Is there a way to start gnome-panel without the "DE managing part", just as regular application?

Or is there any other way to combine the above mentioned features?

Hope someone of you can help ;-)

I'm using Ubuntu 12.04 btw.

---

### Post by AlbertJB on 2012-06-27
I work with Gnome classic no effects in Ubuntu 12.04 and the only feature I'd like to add is the HUD. Appart from that, nothing else, happy as when I worked with Ubuntu 10.10.

---

### Post by Frogs Hair on 2012-06-27
The link be of interest. It is easy to create a list of must have features but difficult to develop a desktop environment.  [http://linuxo.com/category/tags/gnome-shell-extensions](http://linuxo.com/category/tags/gnome-shell-extensions)

---

### Post by sondraparkin on 2012-06-27
You could try OpenBox
It has a very highly customization feature
[https://wiki.archlinux.org/index.php/Openbox](https://wiki.archlinux.org/index.php/Openbox)

---

### Post by mojo2012 on 2012-06-28
I'd really like to work with Gnome Classic, but as said, I want a modern window manager. Taskbars are dead!

Today I managed to start the plain old gnome-panel in Gnome Shell. This gives a global menu and the notification indicators on top of gnome shell.
I installed gnome shell extensions that hide the top bar and move the "show overview" hotcorner to the bottom left.

This works really greate so far, except for one time where gnome-panel crashed.

The last remaining wishes are:
* Add a workspace switcher/pager to my second monitor
* Add a shadow to the gnome panel (this can easily be done with compiz, but with mutter?

@Gosset Inofensiu: maybe you can launch gnome-panel above unity too. This could retain the unity dash and HUD functionality but hide the top panel. Then hide the launcher and you're fine ;-)

@sondraparkin: I did a quick google search and it seems that OpenBox doesn't support the features I want.

---

### Post by markbl on 2012-06-28
I'd just remove any foreign stuff, add the gnome 3 team ppa, clean install back to gnome-shell 3.4.1, and then trawl through [https://extensions.gnome.org/](https://extensions.gnome.org/) to set up your environment as you want. There are a stack of extensions there to add docks, switchers, menus, etc - i.e. add back gnome 2/traditional UI features. Surely you can find what you want?

---

### Post by hictio on 2012-06-28
Perhaps you can start with something like [Ubuntu GNOME Shell Remix](http://ubuntu-gs-remix.sourceforge.net/p/home/) and build your perfect Desktop from a GNOME Classic sesion?
Personally, I've tried GNOME Shell, GNOME Classic & Cinnamon (Linux Mint) and neither fully convinces me... Switching to Scientific Linux and plain old and beautiful GNOME 2.

---

### Post by mojo2012 on 2012-06-29
Hi guys,

another cornerstone of my perfect ubuntu setup is ready: I managed to start the unity launcher inside gnome shell.

My setup now looks like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=220407&stc=1&d=1340969505[/IMG]

Bugs:
* Sometimes the unity dash pops up when pressing the <super> key
* ubuntu dash button still there
* switch workspace button is still there

But I'm quite sure I'll fix the last remaining bugs to ;-)

Thanks for all your input so far.

---

### Post by AlbertJB on 2012-07-08
Hmmm a little weird shuch combination no? And what about working with several windows opened alltogether, is it usable to work in this situation in your case?

> **mojo2012 said:**
> Hi guys,

another cornerstone of my perfect ubuntu setup is ready: I managed to start the unity launcher inside gnome shell.

My setup now looks like this:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=220407&stc=1&d=1340969505[/IMG]

Bugs:
* Sometimes the unity dash pops up when pressing the <super> key
* ubuntu dash button still there
* switch workspace button is still there

But I'm quite sure I'll fix the last remaining bugs to ;-)

Thanks for all your input so far.

---

### Post by markbl on 2012-07-08
> **mojo2012 said:**
> 
another cornerstone of my perfect ubuntu setup is ready: I managed to start the unity launcher inside gnome shell.

I don't see the point. If you like the Unity launcher so much then may as well just run Unity. Use ccsm to assign scale view to top left hot corner which makes Unity more like gnome shell.

Such an unnatural environment like this will be very fragile and will break every second update, etc.

---

### Post by AlbertJB on 2012-07-08
+1

Although I insist on the fact that I don't feel comfortable working with 8 or 10 open windows both in Gnome shell or Unity. I gave them a try, but that's not the point of the thread.

I like Unity's HUD and I'd like to add it to gnome-classic, but we are at the same point, so :p

> **markbl said:**
> I don't see the point. If you like the Unity launcher so much then may as well just run Unity. Use ccsm to assign scale view to top left hot corner which makes Unity more like gnome shell.

Such an unnatural environment like this will be very fragile and will break every second update, etc.

---

### Post by AlbertJB on 2012-07-08
Sorry @mojo2012, I didn't see your response. I already did that, but it didn't work cause I work with different panels on bottom and on left :( 

> **mojo2012 said:**
> I'd really like to work with Gnome Classic, but as said, I want a modern window manager. Taskbars are dead!

Today I managed to start the plain old gnome-panel in Gnome Shell. This gives a global menu and the notification indicators on top of gnome shell.
I installed gnome shell extensions that hide the top bar and move the "show overview" hotcorner to the bottom left.

This works really greate so far, except for one time where gnome-panel crashed.

The last remaining wishes are:
* Add a workspace switcher/pager to my second monitor
* Add a shadow to the gnome panel (this can easily be done with compiz, but with mutter?

@Gosset Inofensiu: maybe you can launch gnome-panel above unity too. This could retain the unity dash and HUD functionality but hide the top panel. Then hide the launcher and you're fine ;-)

@sondraparkin: I did a quick google search and it seems that OpenBox doesn't support the features I want.

---

### Post by markbl on 2012-07-08
> **Gosset Inofensiu said:**
> Although I insist on the fact that I don't feel comfortable working with 8 or 10 open windows both in Gnome shell or Unity. I gave them a try, but that's not the point of the thread.
But a large number of open windows was/is more awkward to manage in that tiny classic/gnome2 style taskbar. I think it is much easier to quickly spot and select them in the greater real-estate scale/super view. So gnome-shell and unity, which exploit our modern graphics cards ability to natively produce that scaled view, are definitely an improvement here IMHO.

---

### Post by AlbertJB on 2012-07-08
OK, this is the Neverending debate about desktop metaphor so... Maybe you are right, I should open my mind and get used to this new concept of GUI since more and more people are adopting these new DE as their default DE (taskbar is dead, I've even read on some other thread). 

But take into account that only 1% of desktop computer users work with Linux, 90% works with Windows. Imagine the distress for that whole community of Microsoft Windows shaped users when first introducing themselves to Linux with such completely renewed DEs :p 

OK, no more posts from me in this thread, thanks for the patience and understanding of a Linux newbie.

---

### Post by markbl on 2012-07-08
> **Gosset Inofensiu said:**
> 
But take into account that only 1% of desktop computer users work with Linux, 90% works with Windows. Imagine the distress for that whole community of Microsoft Windows shaped users when first introducing themselves to Linux with such completely renewed DEs 
Well I have not looked at windows since XP days so I have no idea where it is at now. However, I do own a current Macbook Air running the latest Lion and the the Apple Mission Control UI is essentially the same as gnome-shell and unity (a bit of a mix of both). I.e. it is also all built around the scale view. You best get with it!

---

### Post by mojo2012 on 2012-07-09
@markbl: The reason why I'd like to mix those 3 elements is that the unity panel is supior to all other panels, even the gnome shell dash. It correctly displays java apps launchers, wine apps like teamviewer, has quicklists and looks great.

The gnome shell dash on the other side doesn't group the windows of most of my java and wine apps (like myeclipse, teamviewer) correctly.

I can pin myeclipse to the dash, but when opened, the icons shows up twice, one launcher, one running app/window icon ...

On the other hand, gnome shell's overview is basically a combination of compiz scale and expo. This is much much better to use than unity's scale and expo ... where e.g. it's so unintuitive to move windows around or to simply select another workspace (double click ...?)

I didn't want to start a debate what's better, more intuitive or more beautiful!

All I wanted to know is, if some of you already know how to make this all work ... I'm now at a point, where everything works like I want it to be - with some theming issues remainding ..

And the whole setup is quite stable too! Once gnome-panel crashed and from time to time the area where the menu in the windows would be are empty (e.g. in filezilla) but shown correctly in the gnome-panel.
Nothing serious so far.
@Gosset Inofensiu: Window management (I use 5 workspaces with ~ 2 windows on each) works great.

---

### Post by markbl on 2012-07-09
> **mojo2012 said:**
> 
The gnome shell dash on the other side doesn't group the windows of most of my java and wine apps (like myeclipse, teamviewer) correctly.

I can pin myeclipse to the dash, but when opened, the icons shows up twice, one launcher, one running app/window icon ...

Funny, I have suffered this bug through Ubuntu 11.04, 11.10, and in 12.04 with Unity, never had it with Gnome shell. Unity also sometimes does not show a running app's icon in the launcher at all (although to be fair it seems this unity bug was finally fixed a month or two ago in 12.04 updates). This bug was one of the motivations for me to move to Gnome shell.

---


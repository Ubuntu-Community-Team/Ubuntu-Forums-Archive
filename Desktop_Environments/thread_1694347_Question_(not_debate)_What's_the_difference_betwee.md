---
title: "Question (not debate): What's the difference between Unity and Gnome Shell 3"
date: 2011-02-24
forum: Desktop Environments
---

### Post by Shepherd X on 2011-02-24
Could someone summarize what the differences between Gnome 3 Shell and Unity are? I know that Ubuntu 11.04 will be using Gnome 3 but not the default Gnome Shell, but rather the Unity shell. I don't have a problem with that. I looked at some screenshots of Gnome 3 Shell and Unity, and really the only thing I noticed between the two are panel icon colors.

It looked like Gnome 3 icons were nicer looking, but that doesn't mean much. I also read some comparisons after doing a Google search.

Could someone explain further the differences?

Also, will Ubuntu 11.04 continue to have 2 panels by default?

---

### Post by TuxIsAwesome on 2011-02-24
Currently if you use the Classic Ubuntu Desktop in 11.04, you will have two panels.

Unity uses Compiz in 11.04, while Gnome Shell (Gnome 3) uses Mutter. There are some other differences but I cant remember what they were right now.

Unfortunately from what I've heard Gnome Shell has broken dependancies in 11.04 which is why it isn't available in the Repos. 

Unity also has a QT based port called Unity 2d which is installable in both 11.04 and 10.10 through a repo. It seems to run faster some times than the 3d version, but it's hard for me to tell for sure.

---

### Post by thekwill on 2011-03-24
I have the same questions. I am trying to build up a list of comparisons at [http://www.wikivs.com/wiki/Gnome_Shell_vs_Unity](http://www.wikivs.com/wiki/Gnome_Shell_vs_Unity) any contributions would be welcome.

---

### Post by Copper Bezel on 2011-03-24
Here are a few things - I'm recycling this answer from a previous discussion.

Unity is Ubuntu's alternative for Gnome Shell. Canonical didn't like the direction Gnome was going, I think partly because they prioritize new users and the intuitiveness of the interface. Also, Canonical hopes to make future versions of Ubuntu tablet-ready, while Gnome Shell is, I think, moving in a touch-unfriendly direction. You can't run both shells on the same system, (because at present) they depend on different versions of Gnome, 2.x vs. 3.x.

Although its development is being managed by Canonical, Unity can be run on any distro that meets the requirements of Gnome and Compiz and is slated to be included in the repos for future iterations of Debian.

Unity and Gnome Shell both depend on Gnome and are simply applications running over a Gnome session (minus a few ordinarily required sessions and services) so there's always the option of logging into a Classic session. This isn't to be confused with a Gnome 2.x session; it just means having a panel (which is no longer receiving updates beyond 2.x but will continue to ship in 3.0) in place of a shell. That is to say, Unity is a shell on Gnome 2.x and will eventually migrate to 3.0 while Gnome Shell is the default shell for 3.x, but Gnome (whether 3.x or 2.x) can always still run a Classic desktop.

Both shells are receiving bad press about a lack of configurability, which is slowly being implemented in Unity within certain restraints and a total unknown in Gnome Shell. Mark Shuttleworth, by all appearances, wants Unity (and by extension Ubuntu) to take on a Mac OSX-like consistency in visual identity and workflow. The left-hand Launcher, for instance, can be set to Intellihide and its icons will eventually support resizing, but it can only appear on the left screen edge, can't be extensively reconfigured to add or remove applets, etc.

Unity will be themed in the usual GTK method and now accepts panel themes; Gnome Shell can't be easily themed yet but is using CSS, which will make themes easy to develop in the near future.

Gnome Shell depends on Mutter (Metacity + Clutter) and conflicts with Compiz, while Unity depends on Compiz with Mutter as a fallback for low-end machines. This means that Unity is normally a Compiz Fusion plugin but conflicts with some old plugins (for instance, the Desktop Cube.) On the other hand, Unity retains a higher degree of visual continuity with Compiz than the Classic desktop. For instance, Expo doesn't treat the new Panel and Launcher as a window tied to a particular desktop, so the panel remains accessible during desktop switching.

In terms of direct usability, Unity uses a more conventional method of task switching, workplace management, and window control, while Gnome Shell uses new features like automatic workspaces and has apparently dropped the idea of minimizing windows altogether.

---

### Post by Ron McIlvaine on 2012-08-31
Wow. For a newbie that is like reading a technobabble script from an old Star Trek TNG episode. There are more acronyms to learn. Thanks. I'm learning.

---


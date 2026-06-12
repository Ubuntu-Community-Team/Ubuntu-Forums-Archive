---
title: "Testing Kubuntu v Xubuntu before updating to 18"
date: 2018-08-04
forum: Desktop Environments
---

### Post by makem2 on 2018-08-04
I am currently using xubuntu on 16.04 and will later update to 18. Before I do that I would like to check out kubuntu which I have never tried.

Following:

[https://ubuntuforums.org/showthread.php?t=2364370](https://ubuntuforums.org/showthread.php?t=2364370)

I installed kubuntu-desktop, choosing lightdm, keeping a list of all packages installed.

I rebooted and expected to be offered a choice of which desktop to use but the usual (apparently) xubuntu sign-in was offered.

The desktop appeared identical to xubuntu, the only difference noted so far was my mouse which I normally use LH (I swap regularly), had changed buttons and appears to be flaky now, not certain which button is left or right sometimes!

Have I missed something? Should there be a choice? Do I have to configure the desktop, taking advantage of the packages installed?

---

### Post by deadflowr on 2018-08-04
Themes and other settings can get murky when you do that.
Which is why it is not recommended to run mixed desktops if you want to get a clean feel for how things run.

Better to download the flavor's installation media, and either run the Try Ubuntu.
Or better yet, resize you hard drive an allocate a small amount of space (25Gb is usually more than enough) to use for testing.
(Basically you set aside some free space, and then during install use the manual/ something else option to configure it to use that space)
This way you keep your current system intact, and have a secondary area that you can test various distros with.
(Secondary hard drives work as well, if you have access to more hard drives than just one)

That aside:
> I rebooted and expected to be offered a choice of which desktop to use but the usual (apparently) xubuntu sign-in was offered.


I'm guessing it's still Xubuntu's login greeter, if so I believe up top should have a dropdown menu item in the login screen's panel that should give you the login options you have, including plasma-desktop, which is what kubuntu desktop is called.
New desktop options have to be manually selected at login.

My 2 cents.
my 2 very rambly cents

---

### Post by makem2 on 2018-08-04
I do have another HD used for data and could install there but I'm afraid it maybe to late for that.

Having kept a list of all packages installed, how would I go about uninstalling them in bulk?

EDIT:

Well, that excursion was short and sweet!

I chose plasma and as far as I am concerned I was given a desktop which reminded me immediately of windows. I want out!

I prefer minimalism, not widget stuff, fancy screens (mine is solid dark green), and look-alike windows menus. (Sorry if I am being to critical with so shorter trial)

I do really need now to uninstall every package! Or, maybe better still, wait until 18 is offered and make a complete new install as my /home is separate.

Which would be the better option?

---

### Post by deadflowr on 2018-08-04
Removing kubuntu-desktop packages can be quite painful.
Though if you have the packages in a list you can try running an apt remove command.
But use the -s flag to do a simulation first.
the simulation will not actually do anything, but will show you what it would be doing.

Something like
```
sudo apt remove -s package1 package2 package3
```
Then you can review the output and see whether what you listed would be the only things it would remove or if it would also try to remove other things.

Unfortunately The kubuntu-desktop package pulls in a very large amount of bloat. So it would be rather task-heavy to review every package that would be removed.
Fortunately that bloat is mostly only storage bloat and should not have an affect on anything else.

(The original system never needed any of what Kubuntu-desktop installed, and so it doesn't need it still.
So basically it's dead weight.
As I posted in the first line of my last post, setting can get murky, but fixing settings should be doable without removing packages.
(well fixable 9 out of 10 times, there is always times when what was pulled in does cause more issues))

> I do really need now to uninstall every package! Or, maybe better still, wait until 18 is offered and make a complete new install as my /home is separate.

I missed this.
Why not download 18.04.1 now, if you're going to do a clean install?
It's been available for days now.

---

### Post by makem2 on 2018-08-04
Thank you deadflowr.

I have removed kubuntu sucessfully.

I have also made a 25GB partition on a HD alongside windows and data (xubuntu is on an SSD).

It occurs to me that this time I should ask what to expect if I install a full kubuntu there to look deeper as I may be able to minimalise it to my liking. However I wonder if the effort would justify not just using xubuntu.

Your comment, "Unfortunately The kubuntu-desktop package pulls in a very large amount of bloat" does not enamor me to it at the moment.

Would choosing which OS to use at login be straightforward? I have never had two linux installed together but would assume grub would give me the choice.

---


---
title: "Cinnamon DE keeps freezing"
date: 2022-04-25
forum: Desktop Environments
---

### Post by mibix2 on 2022-04-25
I have been having this problem for like a year now and have been forced to mostly use other DEs even though I'm not a fan at all.  After running for about a day I have an issue where I can still move the mouse around but can't click anything and nothing seems to be updating, it is all just frozen.  I can't even alt+F2 or any of the other alt+F key combos. I have updated my kernel to 5.17.4 using this repo as I read some older kernels  have issues with Cinnamon [https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline](https://launchpad.net/~tuxinvader/+archive/ubuntu/lts-mainline) . I am using a Zetac Gefore GT 710 GPU and am on ubuntu 20.04.  I also updated Cinnamon to the most recent version using this repo as I thought that might be the issue [https://launchpad.net/~wasta-linux/+archive/ubuntu/cinnamon-4-8](https://launchpad.net/~wasta-linux/+archive/ubuntu/cinnamon-4-8) . Here are my xsession error logs not really sure what they mean though heh:
[https://paste.ubuntu.com/p/TrGF5RVsdj/](https://paste.ubuntu.com/p/TrGF5RVsdj/)
[https://paste.ubuntu.com/p/73Sw7HC393/](https://paste.ubuntu.com/p/73Sw7HC393/)


If there is any other info you need let me know and I can provide it.

---

### Post by DuckHook on 2022-04-26
Welcome to the forums, mibix2

When you install something through a PPA, especially something as foundational as your DE, it is very difficult for forum members (who practically universally run more mainstream DEs based on official flavours) to help.

[LIST=1]
[*]Most Linux users are very security conscious. We don't add PPAs to our systems unless we are absolutely sure about their security bona fides. Few of us would feel safe adding this PPA to our systems.
[*]The PPA you link to is not current. The last update was over a year ago.
[*]Rather than mixing and matching various components and then praying that everything works together, try Ubuntu Cinnamon Remix: [https://ubuntucinnamon.org/](https://ubuntucinnamon.org/)  It's unofficial, but at least the maintainers have done much of the heavy lifting for you by presumably squashing a bunch of bugs and incompatibilities already.
[*]Alternatively, install an older more stable version of Ubuntu Server (like Focal), then add only the Cinnamon DE within that repo. Presumably, it has been tested for compatibility. Do *NOT* change the kernel or otherwise monkey with the base OS.
[*]Do *NOT* install Cinnamon on top of an existing DE. This is frequently the cause of irritating incompatibilities that are difficult to diagnose. For a more detailed explanation as to why mixing DEs is a bad idea, see the link in my sig: The Best 'buntu Flavour.
[*]Why use Ubuntu? If you prefer Cinnamon, why not use the distro that invented and maintains it? Install MINT instead.
[/LIST]
While Ubuntu makes it possible to run the Cinnamon DE, you should realize that your decision to do so automatically means a limited circle of help. You will perforce place yourself into an edge case user space.

---


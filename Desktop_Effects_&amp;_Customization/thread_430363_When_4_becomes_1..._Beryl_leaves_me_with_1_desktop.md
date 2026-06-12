---
title: "When 4 becomes 1... Beryl leaves me with 1 desktop"
date: 2007-05-02
forum: Desktop Effects &amp; Customization
---

### Post by QwUo173Hy on 2007-05-02
After enabling desktop effects, I had a cube and I noticed on the bottom right of the screen that there is no longer the spaces between the desktops like in previous versions of Ubuntu. Very nice.

Moments later, I could not rotate the cube and I seemed to have lost access to applications that were on those desktops. When I looked at the pager again, there was only one desktop!

I tried re-enabling desktop effects but it was no use. I disabled the effects and increased the number of desktops to 4 which gave me the old style pager again (as in Dapper / Edgy). I then tried re-enabling desktop effects, but the number of desktops went back down to 1 again.

If someone has a fix for this, I'd love to get it working and report a bug (something I've never done).

I am just a user on this machine and don't have Admin access, but the graphics card is an NVidia with at least 128 MB ram and the computer itself has about 2 GB ram.

Thanks for reading,
Jarlath

<edit> I say Beryl, but I don't know if it's Beryl or Compiz that comes with Feisty?</edit>

---

### Post by KIAaze on 2007-05-02
> **jarlath said:**
> 
<edit> I say Beryl, but I don't know if it's Beryl or Compiz that comes with Feisty?</edit>

It's Compiz.

I had the same problem on my compaq laptop with an ATI card.
But I solved it by installing the following packages:
compiz-extra
compiz-gtk

Hope it helps. ;)

You may also want to try out the other packages eventually:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=compiz&searchon=names&subword=1&version=feisty&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=compiz&searchon=names&subword=1&version=feisty&release=all")
(You can also search for them in the synaptic package manager of course: Search for "compiz")

edit:
> I am just a user on this machine and don't have Admin access, but the graphics card is an NVidia with at least 128 MB ram and the computer itself has about 2 GB ram.

In that case, you should contact the admin. That should be easier (and better for the other users too) than trying to solve the problem as a user.

---

### Post by Fell on 2007-05-02
This happened to me a couple of times the first time I tried the desktop effects in feisty too. You can get the cube back by typing gconf-editor into the terminal.

Go into apps , compiz, general, screen0, options.

Find where it says hsize and change the value to 4.

Hope this helps.

---

### Post by QwUo173Hy on 2007-05-03
Thanks guys, that's great. I may install Feisty on my Edgy machine now. I'm not into effects really, but the desktop effects actually help me work better when there are a lot of apps open so I'd like to have it.

Thanks again,
Jarlath

---


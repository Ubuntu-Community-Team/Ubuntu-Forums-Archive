---
title: "Prevent Gnome extensions breaking after updates"
date: 2019-09-23
forum: Desktop Environments
---

### Post by anticloud on 2019-09-23
I have already used Ubuntu long ago and also I have been using Linux Mint but now I wish to use Ubuntu official flavor that is Gnome. I would use the 18.04 LTS version.
 
I would be customizing Gnome with extensions, tweak tool but I have read that extensions usually break up after updates. 

Are there any extensions powerful enough to withstand break up after updates? If not is there some way to prevent extensions from breaking up?:)

---

### Post by cruzer001 on 2019-09-23
> I have read that extensions usually break up after updates. 
I have not read this.  Link please

---

### Post by anticloud on 2019-09-24
> **cruzer001 said:**
> I have not read this.  Link please

I have read that but am unable to find the sites as yet but more than reading I have watched some YouTube videos which say that. I will search and post the links for your view.

---

### Post by uRock on 2019-09-24
I didn't run many extensions when I was using gnome, just weather and a few others. On Debian Buster and Ubuntu 18.04, neither had issues with updates breaking the extensions.

---

### Post by anticloud on 2019-09-24
> **uRock said:**
> I didn't run many extensions when I was using gnome, just weather and a few others. On Debian Buster and Ubuntu 18.04, neither had issues with updates breaking the extensions.


That&#8217;s great to know. I would be using 18.04 Gnome version but personally I don&#8217;t like Gnome&#8217;s default interface or I should better call it Ubuntu&#8217;s customized interface. So I intend to give it a traditional look like Windows, Cinnamon, Kde etc. 

But first I wish to know if those extensions break up easily or are strong enough to continue working etc. Your reply is the first I have received and it&#8217;s positive. 

I am looking forward to just a few more positive replies and I will be using Ubuntu as well as begin to love love Gnome. :)

---

### Post by uRock on 2019-09-24
This may be helpful for you. I haven't tried it, yet. I don't like Ubuntu's Gnome, either. [https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-install-vanilla-gnome-on-ubuntu-18-04/](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-install-vanilla-gnome-on-ubuntu-18-04/)

---

### Post by anticloud on 2019-09-24
> **uRock said:**
> This may be helpful for you. I haven't tried it, yet. I don't like Ubuntu's Gnome, either. [https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-install-vanilla-gnome-on-ubuntu-18-04/](https://www.serverlab.ca/tutorials/linux/administration-linux/how-to-install-vanilla-gnome-on-ubuntu-18-04/)

uRock, I think you misunderstood. 

Actually what I said is that I don’t like vanilla Gnome as well as Ubuntu’s customized Gnome. So I wish to give it a traditional look like Cinnamon, Mate or Windows. 

Anyway thanks for your link. :)

---

### Post by uRock on 2019-09-24
Why not just use Cinnamon or Mate, instead making gnome look like them? Google tells me those two don't use gnome extensions, though I could be wrong.

---

### Post by Dennis N on 2019-09-24
> I wish to know if those extensions break up easily or are strong enough to continue working etc.

We are talking about updating using Software Updater to a new Ubuntu version. It depends on the extension if they work or not. Many continue working. Best approach is to uninstall all extensions you have installed yourself before you upgrade with Software Updater. Then after upgrading Ubuntu, reinstall the instensions one-by-one using the version matching the new gnome shell version*. Otherwise, gnome-shell may not start. Extensions don't automatically upgrade when you upgrade gnome shell. It's the responsibility of the extension's developer to keep them up to date. Sometimes, they don't get it done - you have to find a substitute or do without. Usually, they have an updated version ready to go if it's needed.

*I manage all extensions through the gnome extensions website. It's easier and you can select the version to install.

[https://extensions.gnome.org/](https://extensions.gnome.org/)

> I have read that extensions usually break up after updates.

Regular software updates don't break gnome-shell extensions. I've never seen that happen. They are only going to break when you upgrade the gnome-shell version, and that's only done when you go to a new Ubuntu version.

---

### Post by anticloud on 2019-09-24
> **Dennis N said:**
> We are talking about updating using Software Updater to a new Ubuntu version. It depends on the extension if they work or not. Many continue working. Best approach is to uninstall all extensions you have installed yourself before you upgrade with Software Updater. Then after upgrading Ubuntu, reinstall the instensions one-by-one using the version matching the new gnome shell version*. Otherwise, gnome-shell may not start. Extensions don't automatically upgrade when you upgrade gnome shell. It's the responsibility of the extension's developer to keep them up to date. Sometimes, they don't get it done - you have to find a substitute or do without. Usually, they have an updated version ready to go if it's needed.

*I manage all extensions through the gnome extensions website. It's easier and you can select the version to install.

[https://extensions.gnome.org/](https://extensions.gnome.org/)



Regular software updates don't break gnome-shell extensions. I've never seen that happen. They are only going to break when you upgrade the gnome-shell version, and that's only done when you go to a new Ubuntu version.


Hi Dennis N,

Thanks a lot for sharing this great valuable information. It has clarified a lot to me about the Gnome extensions. It&#8217;s also nice to know that that the extensions don&#8217;t break if one remains on the same Ubuntu version. 

That&#8217;s a plus for Ubuntu as it has a fixed release model. I think extensions would break often if one uses some distro based on the rolling release model like Manjaro. 

I think Gnome developers should include Gnome extensions, tweak tool etc. in Gnome as default part of their desktop. May be they do that in Gnome 4. 

Anyway is that possible to know whenever an update is released and update the extensions? Kindly inform. Best regards. :)

---

### Post by Dennis N on 2019-09-24
> Anyway is that possible to know whenever an update is released and update the extensions? Kindly inform.
Sometimes I get a notification, but you can check at the gnome extensions web page. See the attached image showing most of my own extensions (two didn't fit in the screenshot). The green icon means there is an upgrade - click that icon to upgrade. Blue icon is to configure the options for that extension. Red icon is to uninstall.  The switch will disable but leave it installed. The "System extensions" can't be changed by the user.

---


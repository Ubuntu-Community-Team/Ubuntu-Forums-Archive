---
title: "Convert Ubuntu install to Xubuntu?"
date: 2012-05-08
forum: Desktop Environments
---

### Post by spoonernash on 2012-05-08
I have an existing Ubuntu install. I tried to adapt to Unity, but it is just too inefficient for a business use desktop. Too hard to switch between apps running in different workspaces. So I installed xubuntu-desktop on top of the Ubuntu installation. I am very happy with the xfce desktop. Can I convert the Ubuntu installation to a Xubuntu installation without doing a clean install? I am looking to reduce the number of unused packages that get updated.

---

### Post by deadflowr on 2012-05-08
Yes you can. All you need to do is install xubuntu-desktop either from the software center, synaptic or terminal.

From the terminal

```
sudo apt-get install xubuntu-desktop
```

When you finish installing, and hopefully it installs fine, reboot and at the login screen click on the cog next to your login name and password and choose xubuntu.
Make sure you don't have automatic login set or else you'll have to logout.
On a side note, you might not even need to reboot after install, just logout and follow the above procedure.

---

### Post by beesthorpe on 2012-05-08
you can just add "Xubuntu desktop system" using the software centre.  To remove follow tutorial available [here]("http://www.psychocats.net/ubuntu/pureubuntu")
Oops deadflowr beat me to it - but it might be worth adding that if, otoh, you want "pure" xubuntu and all trace of standard Ubuntu banished Pscyhocats also has a [tutorial on that]("http://www.psychocats.net/ubuntu/purexubuntu")

---

### Post by vasa1 on 2012-05-08
OP has already installed xubuntu desktop. What remains is to remove software that is no longer needed by running xfce.

Edit:
Oops! The psychocats link should do it.

---

### Post by spoonernash on 2012-05-08
Thanks for the replies. I already have xubuntu-desktop installed. I would like to uninstall the unused parts of ubuntu-desktop (unity, evolution, etc).

---

### Post by mips on 2012-05-08
See [http://ubuntuforums.org/showthread.php?t=416802&page=8](http://ubuntuforums.org/showthread.php?t=416802&page=8)

or if you want the latest XFCE 4.10 see [http://ubuntuforums.org/showthread.php?t=1972548](http://ubuntuforums.org/showthread.php?t=1972548)

---

### Post by vasa1 on 2012-05-08
Hmmm, looking at those links ... Seems a bit early to go down that road for those of us who aren't really into "testing".

I guess it's safer to do a clean Xubuntu install if one wants Xubuntu.

---

### Post by mips on 2012-05-08
> **vasa1 said:**
> Hmmm, looking at those links ... Seems a bit early to go down that road for those of us who aren't really into "testing".

I guess it's safer to do a clean Xubuntu install if one wants Xubuntu.

Not really testing seeing it's final release on the xfce side, working fine here. I installed it from a base xubuntu 12.04 install done vie the alternate cd image.

A clean install is always a good idea.

---

### Post by kansasnoob on 2012-05-08
> **vasa1 said:**
> Hmmm, looking at those links ... Seems a bit early to go down that road for those of us who aren't really into "testing".

I guess it's safer to do a clean Xubuntu install if one wants Xubuntu.

+1!

No idea why ***mips*** is quoting page #8 of a tutorial when that page dates back to 2007 :(

I'm working as quickly as I can to make some recommendations to Aysiu regarding DE conversions but the shift to lightdm has presented problems, as well as causing us to look at other potential flaws :(

There is a reason that the "playing around" section of [Psychocats]("http://www.psychocats.net/ubuntu/") now does not show any "pure DE" conversions :)

Please stop posting links to archived pages!

---

### Post by kansasnoob on 2012-05-08
Somewhat off-topic but you also can get Ubuntu 12.04 LTS to perform nearly the same as the familiar gnome 2 DE:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

---

### Post by dentaku65 on 2012-05-08
> **kansasnoob said:**
> +1!

No idea why ***mips*** is quoting page #8 of a tutorial when that page dates back to 2007 :(

I'm working as quickly as I can to make some recommendations to Aysiu regarding DE conversions but the shift to lightdm has presented problems, as well as causing us to look at other potential flaws :(

There is a reason that the "playing around" section of [Psychocats]("http://www.psychocats.net/ubuntu/") now does not show any "pure DE" conversions :)

Please stop posting links to archived pages!

The correct link for "pure" on Psychocats is:
[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)
and stated for Precise

---

### Post by mips on 2012-05-09
> **kansasnoob said:**
> 
No idea why ***mips*** is quoting page #8 of a tutorial when that page dates back to 2007 :(

There is a reason that the "playing around" section of [Psychocats]("http://www.psychocats.net/ubuntu/") now does not show any "pure DE" conversions :)

Please stop posting links to archived pages!

The thread was started in 2007 and has been continually updated. Page 8 which is the last page I see (forum settings for posts per page) and has info pertaining to the OP's question on 12.04.

Where did I post a link to archived pages?

What exactly is the problem?


> **dentaku65 said:**
> The correct link for "pure" on Psychocats is:
[http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)
and stated for Precise

I posted a link to a thread dealing with the 12.04 issues. I never posted a link to the psychocats site.

---

### Post by spoonernash on 2012-05-09
> **kansasnoob said:**
> Somewhat off-topic but you also can get Ubuntu 12.04 LTS to perform nearly the same as the familiar gnome 2 DE:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

I hold off on new versions, mostly because vmware is a critical app for us and they seem to lag sometimes. Also, now I like the xfce so much I don't think I want to go back.

---

### Post by spoonernash on 2012-05-09
The Psychocats links were very helpful. Thanks.

---

### Post by dentaku65 on 2012-05-10
> **mips said:**
> ...

I posted a link to a thread dealing with the 12.04 issues. I never posted a link to the psychocats site.

I was replying to kansasnoob
> There is a reason that the "playing around" section of Psychocats now does not show any "pure DE" conversions
not to you.

---

### Post by vasa1 on 2012-05-10
```
sudo apt-get install xfce4 xfce4-goodies
```and we're all set and, at login, I can now choose from GNOME, GNOME Classic, GNOME Classic (No effects), Ubuntu, Ubuntu 2D **and** Xfce Session. Now to tweak the looks a bit.

---


---
title: "Gnome 3 - User theme extension not enabled"
date: 2011-05-01
forum: Desktop Environments
---

### Post by Mr.Anarchy on 2011-05-01
Today I did a clean install for ubuntu 11.04. Having seen the power of Gnome 3 (with Fedora) I installed it right away. Some minor problem arose and I had to deinstall accessibility themes and install the "standard" gnome themes.

However there is one more problem and I've added a screen shot to show the problem. As you can see, the gnome desktop seems pretty cool but however the tweak tool doesn't show properly (empathy and other apps neither).

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=190702&stc=1&d=1304276291[/IMG]

Besides the fact that the themes don't properly show in this screen I also get the error "User Theme extension not enabled" now I get the feeling these problems are related, but how do I fix it?

If anyone can give any idea's I'd be very grateful, I've searched everywhere but as far as I know I seem to be the only one with this problem. I would love to take the full advantage of a Gnome 3 desktop but this is getting to be a big "bump" in the road.

---

### Post by Drew93 on 2011-05-01
I have the same problem!

---

### Post by Mr.Anarchy on 2011-05-01
Great to know I'm not alone^^

There's also a few things I have done to try and fix it btw:

- Manually installed the "Adwaita" theme in ~/.themes
- Search the repos for anything "theme" related to enable shell theme
- Searched the entire gconf-editor for something enabling the option

So far no luck.

---

### Post by revoltism on 2011-05-01
I am not sure that is related. Theming is not entirely supported right now. If i remember correct it was the same in Fedora. However.. if you look in "interfaces" instead you can change the metacity and icon-theme.

For Mutter there is another solution. Just go and get [Theme Selector]("http://www.webupd8.org/2011/04/themeselector-gnome-shell-extension-to.html").

---

### Post by Mr.Anarchy on 2011-05-01
Ok, something weird seems to have fixed it. I was playing around with the GTK+ themes and I selected one of the other option (myst for instance) and trying to change it again also revealed the "Adwaita" theme, I selected it and everything was working properly.

I do not know whether the fact that I had earlier also installed "Adwaita"by hand or not but here is a link to download it:

[http://ubuntuforums.org/showpost.php?p=10655293&postcount=86](http://ubuntuforums.org/showpost.php?p=10655293&postcount=86)

Maybe Drew93 can confirm this working cause in that case it just seems like glitch. Could anyone confirm to us know whether going through the themes might glitch and reveal the right theme (with and without manually installing)?

Besides that, thanks for your reply revoltism, but I wasn't really looking to change the mutter theme I just wanted the default GTK+/Metacity theme to work :)

---

### Post by Drew93 on 2011-05-01
Sorry i'm italian and i don't understand some things xd how can i get the gnome shell extension?? i have an other question...ubuntu doesn't install the gnome-shell-extension-common beacuse i haven't the bar at the right of the desk...maybe for me it's all collegated?

---

### Post by mikegioia on 2011-06-08
@Mr.Anarchy, the Adwaita download in there worked like a charm. i had to put it in /usr/share/themes though, not in .themes.

thanks!

---

### Post by cbowman57 on 2011-06-08
Temporarily add a ppa, ricotz/testing, update then use synaptic to add the extensions, I think he has all the one's gnome.org git has packaged as .debs.

Then deactivate the ppa.  You may have need for it later but you don't want to use it on a regular basis, at least not for now.

---

### Post by nitin.pant on 2011-06-09
Thanks, adding ricotz/testing works. I have user themes enabled now.

---

### Post by 1longtime on 2011-06-15
Thanks cbowman57!

So to be more specific with the commands, here's what I did to enable user theme extension:

```

$ sudo add-apt-repository ppa:ricotz/testing
$ sudo apt-get update
$ sudo apt-get install gnome-shell-extensions-user-theme

(if you don't already have ppa-purge installed)
$ sudo apt-get install ppa-purge

$ sudo ppa-purge ppa:ricotz/testing

```

You should now have user extensions enabled (you can verify in the gnome-tweak-tool).

I expect adding PPAs will be unnecessary in the future.

---

### Post by cbowman57 on 2011-06-15
I just toggle it off in the repository but that works too.  What's important, to me, is that people get to enjoy the full functionality of Gnome shell through the use of available extensions & themes.

If anyone is looking for a fully functional Gnome 3.0 shell on Ubuntu just click the link in my signature.

Despite what it might look like, this thumbnail is Gnome shell.

---

### Post by Seventh Reign on 2011-09-22
> **1longtime said:**
> Thanks cbowman57!

So to be more specific with the commands, here's what I did to enable user theme extension:

```

$ sudo add-apt-repository ppa:ricotz/testing
$ sudo apt-get update
$ sudo apt-get install gnome-shell-extensions-user-theme

(if you don't already have ppa-purge installed)
$ sudo apt-get install ppa-purge

$ sudo ppa-purge ppa:ricotz/testing

```

You should now have user extensions enabled (you can verify in the gnome-tweak-tool).

I expect adding PPAs will be unnecessary in the future.

Why would you purge the PPA?  Doing that reverts any changes you just made.  It removes anything added or upgraded by that PPA.

---

### Post by cbowman57 on 2011-09-27
> **Seventh Reign said:**
> Why would you purge the PPA?  Doing that reverts any changes you just made.  It removes anything added or upgraded by that PPA.


Good question, not sure if I was replying to two different threads and got them confused or what.  You are right, purging would undo the changes made by adding the ppa.

I think my intent was explaining to the OP how to activate the testing ppa, install some select packages then deactivate the ppa.

---

### Post by tomasijeaux on 2011-09-30
Damn, I installed user theme extension from ricotz ppas, but the Tweak tool still says user theme extension not enabled:( I upgraded from Natty to Oneiric. In Natty, everything worked just fine for me. Any ideas what could have gone wrong?
Thanks

Update: User theme extension started to work(I have no idea why), but system crashes when I search for something using Dash. I had to turn this extension off. I guess it might have something to do with new fresh of Gnome 3.2. Or I don't know

---


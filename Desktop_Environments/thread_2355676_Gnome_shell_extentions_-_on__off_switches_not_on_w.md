---
title: "Gnome shell extentions - on / off switches not on website"
date: 2017-03-15
forum: Desktop Environments
---

### Post by mrwaistcoat on 2017-03-15
Hi all,

Just done fresh Gnome install and have problem not seen before.

I've followed all the steps to install extensions (browser add ons etc) and have not had a problem with previous install. Strangely, the [https://extensions.gnome.org/](https://extensions.gnome.org/) it not showing the on/off switch for me to add.  Neither can it list my added extensions.

Wondering if this is just me or a wider problem?  If it's just me, any advice appreciated!

Thanks

---

### Post by ajgreeny on 2017-03-15
Which browser?

It is difficult to know what answers we can give you with the information you have given us so far.

---

### Post by tea for one on 2017-03-15
> **mrwaistcoat said:**
> Hi all,

Just done fresh Gnome install and have problem not seen before.

I've followed all the steps to install extensions (browser add ons etc) and have not had a problem with previous install. Strangely, the [https://extensions.gnome.org/](https://extensions.gnome.org/) it not showing the on/off switch for me to add.  Neither can it list my added extensions.

Wondering if this is just me or a wider problem?  If it's just me, any advice appreciated!

Thanks

Are you using Firefox 52? If you are, then it is a wider problem with a solution.

It is something to do with NPAPI plugins (If I knew how they worked, I'd elaborate but it's out of my comfort zone)

Anyway, here are a couple of helpful links:-

[https://blogs.gnome.org/ne0sight/2016/12/25/how-to-install-gnome-shell-extensions-with-firefox-52/](https://blogs.gnome.org/ne0sight/2016/12/25/how-to-install-gnome-shell-extensions-with-firefox-52/)

[http://www.omgubuntu.co.uk/2017/01/install-gnome-shell-extensions-firefox-chrome](http://www.omgubuntu.co.uk/2017/01/install-gnome-shell-extensions-firefox-chrome)

Kind regards

---

### Post by mrwaistcoat on 2017-03-15
Issue is the same both with Firefox and with Chrome

---

### Post by mrwaistcoat on 2017-03-15
Both browsers give a message re native host connector not installed.

I've done
sudo apt-get install chrome-gnome-shell
but it's already installed

---

### Post by tea for one on 2017-03-15
> **mrwaistcoat said:**
> Both browsers give a message re native host connector not installed.

I've done
sudo apt-get install chrome-gnome-shell
but it's already installed

The instructions were buried in the links provided earlier


```
sudo add-apt-repository ppa:ne0sight/chrome-gnome-shell
```

```
sudo apt-get update && sudo apt-get install chrome-gnome-shell
```

---

### Post by mrwaistcoat on 2017-03-16
> **tea for one said:**
> The instructions were buried in the links provided earlier


```
sudo add-apt-repository ppa:ne0sight/chrome-gnome-shell
```

```
sudo apt-get update && sudo apt-get install chrome-gnome-shell
```

**Many thanks**, that's resolved it.   This action resulted in an update. What threw me is that chrome-gnome-shell was already installed upon installation, so I assumed it would be the latest as the system had been updated.

---

### Post by uNoubu8a on 2017-03-18
Just ran into this myself.  Not ideal to have to resort to 3rd party repo's but at least we can get our extension fix :)

---


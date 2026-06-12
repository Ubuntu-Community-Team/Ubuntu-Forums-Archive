---
title: "cairo dock icons don't display properly in jaunty?"
date: 2009-04-24
forum: Desktop Environments
---

### Post by mireson on 2009-04-24
Just upgraded to Juanty via update manager. Mostly going great. good work peoples!

**My problem:** there seems to be a problem with my cairo dock's display. Each of the icons displays with a very thin light & flickery border. This has only happened since the upgrade, and no other rendering on my system is affected so far.

Is this a bug? has anyone else experienced it? I've googled & searched the forum and no one else seems to be asking about it.

I'm running an old compaq n610c laptop with an ATI mobility 128MB card (m7 LW). In case that's important.

I'm just using the cairo-dock package installed via synaptic. And the problem persists regardless of theme.

any ideas?

---

### Post by Penguin Guy on 2009-04-24
Presumably you have an Intrepid Cairo dock, try uninstalling it and then installing a Jaunty one.

[COLOR="Red"]Note: The below tutorial was designed for releases between 7.10 and 8.10[/COLOR]
> Add the Cairo-Dock repository to your sources; open the sources.list file:
```
sudo gedit /etc/apt/sources.list
```
Then add the appropriate repository to the end of the file:

deb [http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu) jaunty cairo-dock

The signed GPG key for identification of the repository is:

wget -q [http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg](http://repository.cairo-dock.org/ubuntu/cairo-dock.gpg) -O- | sudo apt-key add -

Then, to install Cairo-Dock, issue these two commands in the terminal:

sudo apt-get update
sudo apt-get install cairo-dock cairo-dock-plug-ins

Note: if you get the error "E: Couldn't find package cairo-dock-plug-ins" try the code below as it seems there has been a name change and the package is now called cairo-dock-plugins in intrepid.
```
sudo apt-get install cairo-dock-plugins
```
[[COLOR="Blue"]Original tutorial here.[/COLOR]]("https://help.ubuntu.com/community/CairoDock")

---

### Post by zip_000 on 2009-05-04
I keep getting this error:

W: Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/jaunty/cairo-dock/binary-amd64/Packages](http://repository.cairo-dock.org/ubuntu/dists/jaunty/cairo-dock/binary-amd64/Packages)  404 Not Found

Now, I can get cairo dock to work, but none of the themes are there, and I don't particularly like the default theme.


What's this about?

Thanks!

---

### Post by onegentleman on 2009-07-24
I have the same problem with Caiuro Dock as mireson. Somebody knows the solution.

---

### Post by mireson on 2009-07-27
haven't been using cairo dock for a while because of this issue. Switched to AWN dock.
Made sure I had the Jaunty dock, still the same display issues.
Will keep using AWN for now. But would prefer to use cairo dock if the display was fixed.

---

### Post by fabounet on 2009-07-27
try insalling CD from the repository or directly from the .deb
also, try launching it with 'cairo-dock -c'

---


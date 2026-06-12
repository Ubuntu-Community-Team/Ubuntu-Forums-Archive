---
title: "Brasero 0.9.0"
date: 2009-01-18
forum: General Help
---

### Post by YMS_1975 on 2009-01-18
I couldn't find an existing thread on this subject, so I thought I'd ask here.

If you visit this link [http://ftp.acc.umu.se/pub/GNOME/sources/brasero/0.9/]("http://ftp.acc.umu.se/pub/GNOME/sources/brasero/0.9/") you'll be taken to Brasero's website.

Apparently they now have Brasero 0.9.0 (unless I'm misunderstanding).
When I went to my Add/Remove... dialog box, I did a search for Brasero but the older version (0.8.2) which is labeled as their "latest stable release" is what is available.

I've tried downloading the newer version, but I've had no luck. Has **anybody** been able to download the newer version for Ubuntu 8.10?

---

### Post by adamlau on 2009-01-18
Downloaded 0.9.0 a few days ago, runs well built against the libburnia libraries only, no coasters as of yet (two CD-Rs, one DVD+R). Ubuntu typically pushes down security only updates for most packages. If you must have the latest and greatest, lurk around on getdeb.net, or build it yourself.

---

### Post by binbash on 2009-01-18
[http://www.getdeb.net/](http://www.getdeb.net/) , get the brasero debs from getdeb.

---

### Post by YMS_1975 on 2009-01-19
> **binbash said:**
> [http://www.getdeb.net/](http://www.getdeb.net/) , get the brasero debs from getdeb.
binbash...

How do I get the debs? Can you give me step by step instructions on how to get the latest version? The link you gave me is the web sites main address.

---

### Post by adamlau on 2009-01-19
It appears that Brasero 0.9.0 has not yet been packaged for release on GetDeb. Give it a few more days, maybe a week. If it still does not show up, you may have to build it yourself. If you happen to do so, I will let you know that Brasero from source is not exactly the easiest build for a beginner to start off with (lots of dependencies, numerous options), but not exactly difficult either. Make sure you have plenty of additional disk space before you begin :) .

---

### Post by meho_r on 2009-01-19
Or maybe try with a PPA like [[COLOR="Blue"]bdrung's[/COLOR]]("https://launchpad.net/~bdrung/+archive") or [[COLOR="Blue"]janvitus'.[/COLOR]]("https://launchpad.net/~janvitus/+archive")

---

### Post by YMS_1975 on 2009-01-21
LOL....

Wow, compiling and PPA's (whatever that may be) is all foreign to me.

I'm really not that well versed with any of the stuff mentioned in your responses. To be perfectly honest, I'm more of a point & click GUI user. I know I should take the time to learn more about how Ubuntu/Linux works but to be honest I'm in no rush; when I need something specific I ask online and learn bit by bit.

So far I haven't had too many problems with Ubuntu (knock on wood) because the **Add/Remove...** feature/application is very easy to use. I just tend to surf the web a lot and like to follow up on the release dates / versions of applications that Ubuntu comes with and noticed that Brasero was updated. So is _Vuze_. But if you go to **Add/Remove...** you'll download an older version of Vuze (same with Brasero). They have 4.0 for linux but I can't seem to update that either.

Unless someone can give me step-by-step instructions I guess I'll wait until the next release. That's one of the things I love about Ubuntu; releases every 6 months.  ;)

---

### Post by meho_r on 2009-01-21
OK, no problem:) Here we go...

We'll install from Benjamin Drung's PPA (Personal Package Archive). If you go on the page I've provided link for, you'll notice a dropdown box at the top ("Display sources.list entries for") in which you should chose your distro version (in our case Intrepid). Below the box are two lines that should be added as Third Party Repository. So, do this:

1. Open Synaptic (System > Administration > Synaptic Package Manager) and enter your user password when requested.

2. In Synaptic go to: "Settings > Repositories".

3. In the newly opened window go to "Third Party Software" tab and click on the "Add" button on the bottom left.

4. Copy the first line from Drung's PPA:
```
deb http://ppa.launchpad.net/bdrung/ubuntu intrepid main

```
Paste it in the empty space and click "Add Source".

5. Repeat step 4. for the second line:
```
deb-src http://ppa.launchpad.net/bdrung/ubuntu intrepid main
```

6. After this you can close that window. You will get a notice that repositories have changed and that you should click on the "Reload" button, so close the notice and click on the "Reload" button on the upper left.

7. Now search for "brasero" and you'll see there is an update (or install Brasero if it isn't already installed).

That's it :)

---

### Post by YMS_1975 on 2009-01-25
> **meho_r said:**
> OK, no problem:) Here we go...

We'll install from Benjamin Drung's PPA (Personal Package Archive). If you go on the page I've provided link for, you'll notice a dropdown box at the top ("Display sources.list entries for") in which you should chose your distro version (in our case Intrepid). Below the box are two lines that should be added as Third Party Repository. So, do this:

1. Open Synaptic (System > Administration > Synaptic Package Manager) and enter your user password when requested.

2. In Synaptic go to: "Settings > Repositories".

3. In the newly opened window go to "Third Party Software" tab and click on the "Add" button on the bottom left.

4. Copy the first line from Drung's PPA:
```
deb http://ppa.launchpad.net/bdrung/ubuntu intrepid main

```
Paste it in the empty space and click "Add Source".

5. Repeat step 4. for the second line:
```
deb-src http://ppa.launchpad.net/bdrung/ubuntu intrepid main
```

6. After this you can close that window. You will get a notice that repositories have changed and that you should click on the "Reload" button, so close the notice and click on the "Reload" button on the upper left.

7. Now search for "brasero" and you'll see there is an update (or install Brasero if it isn't already installed).

That's it :)


Hmmmm....that's odd; I followed your steps to the tee, but it didn't work. Everything up to step #6 worked like a charm. When I went on to step #7, it failed at step #7.  :(

---

### Post by mb_webguy on 2009-01-25
That PPA (as all Launchpad PPAs soon will be) is signed, so you need to add the key.  If you notice on the PPA page, it says "This repository is signed with" followed by a sting of letters and numbers.  Click on that link, and it will take you to a page with the PPA's key.  Right-click the key id link and select "Save as..." to save it to your computer.  Now, in the Software Sources window, click the "Authentication" tab, and then click the "Import Key File" button and locate the file you just saved.  Once you've done this, then everything should work as the earlier post described.

---


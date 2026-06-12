---
title: "[Tutorial]install gimp 2.6 on ubuntu 8.04 (Hardy Heron)"
date: 2008-12-03
forum: General Help
---

### Post by nakama85 on 2008-12-03
[I]Note: Gimp 2.6 is not officially supported by Ubuntu 8.04 Hardy.
However I find that the version provided is useless in comparison. 
Furthermore I see no reason that you should only be able to get *Gimp 2.6* if you use Intrepid. 
I use gimp a lot and have yet to have any issues with this instal. Please also note this is for32bit systems onlyl[/I]

First you will need to add the _getdeb_ source to your source list.

You can do this by opening terminal and entering the following code
```
gksudo gedit /etc/apt/sources.list
```
In the page that opens add this line to the end.
```
deb http://ubuntu.org.ua/ getdeb/
```

Click on save then close the window

Now we need to update our sources.

In terminal enter the following command
```
sudo apt-get update
```

After the update finishes (this should not take long at all)
Now we can Install *Gimp 2.6*

Enter the following command in terminal
```
sudo apt-get install gimp
```

**Congrats. You now have _Gimp 2.6_**

_*Note: This tutorial is almost a direct copy from the tutorial at ubuntugeek.com that can be found*_ [**HERE**]("http://www.ubuntugeek.com/how-to-install-gimp-261-on-ubuntu-804-hardy-heron.html"). 
*_However I believe in unity and I believe that you should not have to go any further than **Ubuntuforums** to find what you are looking for._*

_Also (this may just be me but) I like to go back into my sources.list and remove what I added after installing my desired software. Just because I am paranoid!!_

---

### Post by shadowtag on 2008-12-04
Thanks nakama85!  I've been using 2.6 on Windows for a while and I was unsure how to do this on Hardy.

I followed your steps, but I get the following error:

```
The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.6.3) but 2.4.5-1ubuntu2 is to be installed
        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
        Depends: libpoppler-glib3 but it is not installable
E: Broken packages
```

Any ideas what to do from here?

Thanks for any help!

---

### Post by nakama85 on 2008-12-04
Are you running 32bit os it ony works on 32. If so I will try to find a workaround.

If not then I am sorry I did not specify that.

> **shadowtag said:**
> Thanks nakama85!  I've been using 2.6 on Windows for a while and I was unsure how to do this on Hardy.

I followed your steps, but I get the following error:

```
The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.6.3) but 2.4.5-1ubuntu2 is to be installed
        Depends: libgtk2.0-0 (>= 2.14.1) but 2.12.9-3ubuntu5 is to be installed
        Depends: libpango1.0-0 (>= 1.21.6) but 1.20.5-0ubuntu1 is to be installed
        Depends: libpoppler-glib3 but it is not installable
E: Broken packages
```

Any ideas what to do from here?

Thanks for any help!

---

### Post by shadowtag on 2008-12-04
> **nakama85 said:**
> Are you running 32bit os it ony works on 32. If so I will try to find a workaround.

If not then I am sorry I did not specify that.

Sorry, I should have included that.  Yes, I'm using a 32-bit system.

Thanks!

(I love your signature by the way!)

---

### Post by nakama85 on 2008-12-05
Ok you can try to install the dependencies on an individual bases.

Here are the deb packages for each.

[http://www.getdeb.net/download/3453/0](http://www.getdeb.net/download/3453/0) -   gimp
[http://www.getdeb.net/download/3453/1](http://www.getdeb.net/download/3453/1) -   libgimp2.0
[http://www.getdeb.net/download/3453/2](http://www.getdeb.net/download/3453/2) -   gimp-data
[http://www.getdeb.net/download/3453/3](http://www.getdeb.net/download/3453/3) -   libbabl-0.0-0
[http://www.getdeb.net/download/3453/4](http://www.getdeb.net/download/3453/4) -   libgegl-0.0-0

Let me know if this works?
(note: now that I look at it the dependiencie are different than those you posted. Perhaps my tutorial is already out of date.
you can find the above installs at this site. [http://www.getdeb.net/release/3453](http://www.getdeb.net/release/3453))
> **shadowtag said:**
> 

(I love your signature by the way!)
Thanks. I am anti-widows now I am free of the death grip Microsoft once had me in!

---

### Post by shadowtag on 2008-12-05
OK, I checked out the getdeb packages.  I tried the 2.6.2 deg files here:
[http://www.getdeb.net/release/3453]("http://www.getdeb.net/release/3453")

Then I tried the 2.6.3 files here:
[http://www.getdeb.net/release/3503]("http://www.getdeb.net/release/3503")

I'm using Hardy and it looks like 2.6.3 is for Intrepid, so that deb package may not be the one for me.

Anyway, here's what finally worked for me.  I downloaded all the 2.6.2 deb packages from [http://www.getdeb.net/release/3453]("http://www.getdeb.net/release/3453") and put them in a temp directory.  Then, I went to that directory in a terminal window and used:

```
sudo dpkg -i *.deb
```

I just fired up Gimp and it seems to be working fine!

Thanks for all your help!

---


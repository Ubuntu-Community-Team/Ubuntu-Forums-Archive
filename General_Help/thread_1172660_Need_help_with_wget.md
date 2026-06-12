---
title: "Need help with wget"
date: 2009-05-28
forum: General Help
---

### Post by JaypeeB on 2009-05-28
Alright, I did a quick search online and here at the forums and have found lots of valuable information on how to use wget, but nothing that quite does what I need.

Alright, I've set up a small server at home to run a cstrike server. There's many map packs available online, however there is someone out there that has generously provided a webserver to host map packs. Since they have a bunch of maps hosted I was hoping to use the "wget" command to download the maps that the server hosts, so my users and I could simple connect there and download the maps without lagging the server.

So my server install directory is ... /usr/hlds/cstrike

The map and map files are all hosted at ... [http://example.com/cstrike](http://example.com/cstrike)

So, what I want to do is download the files from the webserver directly into the cstrike folder on my server. Does anyone know how to do this.

So far I've got ... wget -r --no-parent [http://example.com/cstrike](http://example.com/cstrike)

but the problem with this is it will download the files to ... /usr/hlds/cstrike/example.com/cstrike instead of /usr/hlds/cstrike

Thank for your time and help!

---

### Post by ntowakbh on 2009-05-28
To choose a directory to download something to from wget, use the -P option.

```
wget -P /directory/you/want/to/save/to http://example.com/file
```

Hope this helps a bit.

---

### Post by JaypeeB on 2009-05-28
> **ntowakbh said:**
> To choose a directory to download something to from wget, use the -P option.

```
wget -P /directory/you/want/to/save/to http://example.com/file
```Hope this helps a bit.

Nope, unfortunately this did not work, what it ended up doing was ...

saved [http://example.com/file](http://example.com/file) to ...

/usr/hlds/cstrike/example.com/file

I would like

/usr/hlds/cstrike/ (contents of file go here)

---

### Post by ntowakbh on 2009-05-28
> **JaypeeB said:**
> Nope, unfortunately this did not work, what it ended up doing was ...

saved [http://example.com/file](http://example.com/file) to ...

/usr/hlds/cstrike/example.com/file

I would like

/usr/hlds/cstrike/ (contents of file go here)

I'm playing with wget as we speak, it is something to do with the -r option to make it recursive.  Do you need to go down multiple directories?

---

### Post by JaypeeB on 2009-05-28
> **ntowakbh said:**
> I'm playing with wget as we speak, it is something to do with the -r option to make it recursive.  Do you need to go down multiple directories?

Yup... there's I need to go down a few maybe max 2 or 3 not 100% sure... but there are files in .../cstrike/maps/ that I'd like to get and a few other places...

worst case I could just download first .../cstrike/ then ...cstrike/maps/ and so on... just open up a bunch of terminal windows.. =)

---

### Post by pedrotuga on 2009-05-28
I am not sure there is a way of skipping the domain folder naming. It's a matter of trying out different options and check for yourself how they behave.
_Always_ read the man page,
[code]man wget[code] it might look too extensive at first, once you get used to them you will wish your girlfriend/boyfriend came with a manpage.


EDIT:the option you are looking for is **-nH** Just checked it now on the manpage.

If that would be available, you could allways put together a small script that would dwonload and them move the folder. It's as simple as I am making it sound like.

EDIT2: **-nd** will omit the website directory structure and download all the files to the same directory at your filesystem. That might be of some use to you, don't know.

---

### Post by ntowakbh on 2009-05-28
> **JaypeeB said:**
> Yup... there's I need to go down a few maybe max 2 or 3 not 100% sure... but there are files in .../cstrike/maps/ that I'd like to get and a few other places...

worst case I could just download first .../cstrike/ then ...cstrike/maps/ and so on... just open up a bunch of terminal windows.. =)

Or after you've downloaded them to the /usr/hlds/cstrike/example.com/cstrike directory, you could always use a mv command to move them up one directory, and the delete the unused example.com directory.

---

### Post by JaypeeB on 2009-05-28
> **pedrotuga said:**
> I am not sure there is a way of skipping the domain folder naming. It's a matter of trying out different options and check for yourself how they behave.
_Always_ read the man page,
[code]man wget[code] it might look too extensive at first, once you get used to them you will wish your girlfriend/boyfriend came with a manpage.


EDIT:the option you are looking for is **-nH** Just checked it now on the manpage.

If that would be available, you could allways put together a small script that would dwonload and them move the folder. It's as simple as I am making it sound like.

EDIT2: **-nd** will omit the website directory structure and download all the files to the same directory at your filesystem. That might be of some use to you, don't know.

Thank you for your repsonse, the -nH does appear to be doing what I wanted. I did look at the manual page, but I was having a tough time getting through it. As for writing a script to do it myself, I wanted something that would make those files accessable right away, vs having to download them all and then move them (couldnt' think of a way of doing this as they downloaded).

thanks again!

---


---
title: "Extreme Picture Finder"
date: 2009-01-24
forum: General Help
---

### Post by hatalar205 on 2009-01-24
Hi! I'm looking for a program like "Extreme Picture Finder". It is a kind program for finding and downloading photos from pre-determined internet sites. Is there a prgram like this in Ubuntu. ****

---

### Post by hatalar205 on 2009-01-30
Anyone there to help.

---

### Post by khedron on 2009-01-30
As far as I know there is nothing that does exactly what this program does. (But I haven't used the program, so I don't know how much it does anyway.) However:

There's an extension for Firefox called DownThemAll ([http://www.downthemall.net/](http://www.downthemall.net/)) which allows you to download all images (or music, etc) linked to on a page, or select only some of them for download.

You could look into wget, which is a command line tool that can search through (recurse) a whole website looking for particular files.

For example, to download all files on a website ending in .jpg or .png, use
```

wget --recursive --accept ".jpg,.png" http://web.site.com

```

You can change the --accept argument to any wildcard for the file name.
You can also use:
--reject to stop downloading some filenames
--include to include a particular directory (e.g. **--include /img** selects that you only want images from [http://web.site.com/img](http://web.site.com/img))
--exclude to exclude a particular directory (e.g. **--exclude /img** allows download of all images except those under [http://web.site.com/img](http://web.site.com/img))

---

### Post by hatalar205 on 2009-01-30
> **khedron said:**
> As far as I know there is nothing that does exactly what this program does. (But I haven't used the program, so I don't know how much it does anyway.) However:

There's an extension for Firefox called DownThemAll ([http://www.downthemall.net/](http://www.downthemall.net/)) which allows you to download all images (or music, etc) linked to on a page, or select only some of them for download.

You could look into wget, which is a command line tool that can search through (recurse) a whole website looking for particular files.

For example, to download all files on a website ending in .jpg or .png, use
```

wget --recursive --accept ".jpg,.png" http://web.site.com

```

You can change the --accept argument to any wildcard for the file name.
You can also use:
--reject to stop downloading some filenames
--include to include a particular directory (e.g. **--include /img** selects that you only want images from [http://web.site.com/img](http://web.site.com/img))
--exclude to exclude a particular directory (e.g. **--exclude /img** allows download of all images except those under [http://web.site.com/img](http://web.site.com/img))
Thanks for your help. But this program is a bit different. It has a search engine. And it find the photos by itself. For example you need a photo of "Lion". You write the engine "Lion" and it searches the internet sites for that item and when he finds it downloads all. Normally it downloads more than 200 photos in a few minutes. I am looking for such kind of program.

---

### Post by khedron on 2009-01-31
*Edit: Whoops, double post.*

---

### Post by khedron on 2009-01-31
I'm afraid I have heard of no such program for Linux. Sorry.

You might be able to piece this together. Google Image search can provide the images, but you can't use DownThemAll directly with it, since the links given on GIS results are links to thumbnails rather than direct to the images. So use [this site]("http://dearcomputer.nl/gir/"), which wraps GIS to make all the images appear on one page, with DownThemAll's one-click mode.

The site has a limitation of only showing the top ~20 images. Apparently its [Greasemonkey script]("http://userscripts.org/scripts/show/36918") also has such a limitation. The problem is that Google fixes its search results page to 20 images (as does Yahoo). Maybe you could look into a repagination add-on for Firefox to fix this?

I realise this solution isn't perfect, but my Google skills couldn't find a program like the one you describe.

---

### Post by hatalar205 on 2009-01-31
Thanks for your suggestion. I think I must ask this to the linux developers. Maybe they can do something. This kind of programs are not known well by even windows' users even though they are only used with windows. But they are really very usefull. If I find a solution I will write here.

---

### Post by MarblePanther on 2009-01-31
Have you tried running it in WINE?

Just a thought...I wouldn't expect it to work

---

### Post by MarblePanther on 2009-01-31
Here's some excellent news for you:

Go into synaptic and install wine.

download extreme picture finder from [http://www.exisoftware.com/](http://www.exisoftware.com/) to your desktop.

Enjoy it!

It works perfectly, i just tried it.

---

### Post by MarblePanther on 2009-01-31
[attach]101667[/attach]

Extreme Picture finder working on my Ubuntu desktop through WINE.

I searched for lion :)

After you install wine, just click on picturefindersetup.exe and set it up.

After you install it, just go to Applications, Wine, Programs, Extreme Picture Finder 3 -- you can make a desktop icon by dragging it to your desktop.

---


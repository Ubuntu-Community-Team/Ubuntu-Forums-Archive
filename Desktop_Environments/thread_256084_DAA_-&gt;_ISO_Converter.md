---
title: "DAA -&gt; ISO Converter"
date: 2006-09-12
forum: Desktop Environments
---

### Post by The Reckoning on 2006-09-12
Anyone know how I can convert DAA files to ISO files?
Is there a program I can install?
Or, does anyone know of a program that can burn DAA files?

Thanks

---

### Post by ohgod on 2006-09-12
Sadly, the only program I could find that was able to handle .daa files is the windows one:  PowerISO.  Perhaps it's possible to run this under Wine, though I haven't tried it.

---

### Post by airtonix on 2006-11-11
Nope i i juast found the linux version, its on the same page as the download link for windows....
to them linux is an afterthought.....and hey when all your addicts are on heroin.....who cares about that wacky green stuff,

---

### Post by hoctro on 2007-04-03
> **The Reckoning said:**
> Anyone know how I can convert DAA files to ISO files?
Is there a program I can install?
Or, does anyone know of a program that can burn DAA files?

Thanks

[http://www.poweriso.com/download.htm](http://www.poweriso.com/download.htm)
    *

      PowerISO for Linux -- This is a free utility for linux which can extract, list, and convert image files (including ISO, BIN, DAA, and other formats).  Type " poweriso -? " for detailed usage information.  File Size: 286KB   Download Now

---

### Post by DRAGONPOWER on 2007-10-19
so ... how exactly do u install poweriso plz? i need it for a daa windows copy

---

### Post by sk8dork on 2007-10-21
> **DRAGONPOWER said:**
> so ... how exactly do u install poweriso plz? i need it for a daa windows copy

it's an executable file. you download it, extract it somewhere, then in a terminal you cd to wherever you extracted the file (easiest to just extract it to your home directory so you don't need to cd when you open the terminal) and you run
```
./poweriso -?
```
and read what it says.

---

### Post by azzis on 2007-11-08
Convert xxx.daa file to xxx.iso:
```
./poweriso convert xxx.daa -o xxx.iso
```

---

### Post by HyperWireD on 2008-02-12
DAA is a proprietary format by [poweriso]("http://www.poweriso.com/download.htm"). I hate that. [http://en.wikipedia.org/wiki/Direct_Access_Archive](http://en.wikipedia.org/wiki/Direct_Access_Archive)

If you hate installing crap software such as the above, there is this freeware available:

**DAA2ISO**:

[http://aluigi.altervista.org/mytoolz.htm]("http://aluigi.altervista.org/mytoolz.htm")

the zip comes with a compiled windows binary, but it also has source code and a makefile to compile on *nix as long as you link to zlib. Works great on windows, havent checked on *nix.

Also you can use **Acetone ISO** which is linux GPL freeware to convert between many formats including DAA to ISO.

[http://linux.softpedia.com/get/Multimedia/Audio/AcetoneISO-16724.shtml]("http://linux.softpedia.com/get/Multimedia/Audio/AcetoneISO-16724.shtml")


further info:[http://groups.google.com/group/comp.sys.mac.apps/browse_thread/thread/7618aebd431ad6f6]("http://groups.google.com/group/comp.sys.mac.apps/browse_thread/thread/7618aebd431ad6f6")
[http://w-shadow.com/blog/2007/09/07/the-daa-file-everything-you-need-to-know/]("http://w-shadow.com/blog/2007/09/07/the-daa-file-everything-you-need-to-know/")

---

### Post by ViralYouth on 2008-03-10
> **azzis said:**
> Convert xxx.daa file to xxx.iso:
```
./poweriso convert xxx.daa -o xxx.iso
```

Actually it's

```
./poweriso convert xxx.daa -o xxx.iso -ot iso
```

---

### Post by datadevelopment.co.uk on 2008-06-07
There's a little prog called DAA2ISO its free and converts daa to iso, Has a simple open dialog box just choose your .daa file and give your new .iso a name. done.

If you need to you can always extract the files from iso using a program like isobuster or winrar or burn the image with most burning tools.

you can find it on Luigi Auriemma's tools page here
[http://aluigi.altervista.org/mytoolz.htm]("http://aluigi.altervista.org/mytoolz.htm")

Hope that helps.

Richard Butler
*Don't ascii me.*

---

### Post by pluckypigeon on 2008-07-05
How would one go about making a GUI for this?

I can use it without but I would like to make one for my own project.

I need something to do!! Could anyone point me in the right direction.

Thanks

---


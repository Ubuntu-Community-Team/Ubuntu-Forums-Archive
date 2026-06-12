---
title: "Extracting data#.cab files"
date: 2006-03-23
forum: Desktop Environments
---

### Post by pacificdrums on 2006-03-23
OK I have a Dlink DWL g510 in my desktop. I can not get the .inf file out of the data1.cab or the data2.cab. Or more correctly I can not open them at all. I have tried cabextractor and unshield. I can't get either one to open these files. if any one knows how to get the .inf file out of these files I would GREATLY appreciate it. O and I am using these files [http://support.dlink.com/products/view.asp?productid=DWL%2DG510#](http://support.dlink.com/products/view.asp?productid=DWL%2DG510#)

---

### Post by nismoskys on 2006-03-23
im not sure.. but i THINK you might be able to just install the driver onto Windows, and then just search through C:/WINDOWS/ for the inf file.. nd copy it over.

---

### Post by pacificdrums on 2006-03-23
OK but how do I know what the file name is of the .inf?:-k

---

### Post by akiro.yamamoto on 2006-03-23
You can use cabextract to extract the file you need from the .cab package.
Use Synaptic to install it....
Hope this info helps... ;)

BTW:
It's command line, you'll have to read the
```

man cabextract

```

---

### Post by pacificdrums on 2006-03-23
OK I got unshield to work. I had my permissions on the file set wrong.:rolleyes:  Cabextract will not extract these files but unshield will.

---


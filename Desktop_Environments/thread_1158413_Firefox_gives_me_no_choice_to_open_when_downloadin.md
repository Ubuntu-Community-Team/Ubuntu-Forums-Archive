---
title: "Firefox gives me no choice to open when downloading rar or zit"
date: 2009-05-13
forum: Desktop Environments
---

### Post by yuki86 on 2009-05-13
Hi i have problem with firefox, when im downloading rar or zip firefox gives me no choice to open file only download, i have fresh install ubuntu 9.04 firefox 3.0.10 and i delete almost everyhing in my home folder and the problem is still there

also now i have no file types like zip or rar in my settings

[[IMG]http://img208.imageshack.us/img208/383/snmekobrazovky1.th.png[/IMG]](http://img208.imageshack.us/my.php?image=snmekobrazovky1.png)

thanks for help.........

[[IMG]http://img217.imageshack.us/img217/6264/snmekobrazovky.th.png[/IMG]](http://img217.imageshack.us/my.php?image=snmekobrazovky.png)

---

### Post by yuki86 on 2009-05-14
bump!

---

### Post by Locutus_of_Borg on 2009-05-14
> **yuki86 said:**
> i delete almost everyhing in my home folderWhy would you do this?


Set the application for handling rar and zip files to be file-roller (/usr/bin/file-roller) and ensure you have the unrar and unzip packages installed from synaptics

---

### Post by yuki86 on 2009-05-14
and where can i set this pls explain? when i click on some rar and open with i set the path to file-roler nevertheless it doesnt help...

HELP!

---

### Post by Locutus_of_Borg on 2009-05-14
can you not open rar files with file-roller?

do you have unrar-nonfree installed?

---

### Post by yuki86 on 2009-05-14
yes i can 

i have unrar: Unarchiver for .rar files (non-free version) package installed

---

### Post by Locutus_of_Borg on 2009-05-14
okay, when you were "deleting everything form your home folder" by chance did you delete stuff from your .mozilla folder?

try adding this to you .mozilla/firefox/*.default/mimeTypes.rdf
```


  <RDF:Description RDF:about="urn:mimetype:handler:application/x-download"
                   NC:alwaysAsk="true"
                   NC:saveToDisk="true">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/x-download"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:application/zip"
                   NC:value="application/zip"
                   NC:editable="true"
                   NC:description="Zip archive">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/zip"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:application/force-download"
                   NC:value="application/force-download"
                   NC:editable="true"
                   NC:description="Zip archive">
    <NC:handlerProp RDF:resource="urn:mimetype:handler:application/force-download"/>
  </RDF:Description>
  <RDF:Description RDF:about="urn:mimetype:handler:application/x-rar-compressed"
                   NC:alwaysAsk="true"
                   NC:saveToDisk="true">
    <NC:externalApplication RDF:resource="urn:mimetype:externalApplication:application/x-rar-compressed"/>
  </RDF:Description>

```

---

### Post by yuki86 on 2009-05-14
no it doesnt help, my system is broken compiz and other stuff doent work im installing ubuntu again a im connecting install to my contemporary home folder, isnt some chance to install new firefox somehow to avoid this problem with rar/zip?

thanks

EDIT i try to add text to /mimeTypes.rdf with no effect, i also deleted almost everything in my home folder, format / and problem is still there...

---

### Post by yuki86 on 2009-05-15
I discovered that I can open rar if there arent from rapidshare I try two rars,

---

### Post by yuki86 on 2009-05-16
bump

---


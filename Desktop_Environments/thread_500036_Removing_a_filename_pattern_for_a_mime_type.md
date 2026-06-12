---
title: "Removing a filename pattern for a mime type"
date: 2007-07-13
forum: Desktop Environments
---

### Post by deavik on 2007-07-13
Hello,

For the extensions ".m" i have conflicting mime types (I checked that using [assogiate]("http://www.kdau.com/projects/assogiate/")) text/x-objcsrc and text/x-matlab (I want them to be the latter). So when I create new files and save them as .m they are not syntax-highlighted right by gedit, etc...

Assogiate doesn't allow me to delete the binding to filename pattern .m for text/x-objcsrc (the remove button is greyed out). Is there any way to fix this annoying little issue?

The mime type is in /usr/share/mime/packages/freedesktop.org.xml

Thanks

---

### Post by deavik on 2007-07-14
anyone?

---

### Post by kdau on 2007-07-31
Hello, I'm the author of assoGiate. Sorry it took so long for me to find this.

Matches in the system database can't be directly removed, but there is a trick to work around them. Open the "text/x-matlab" type, go to its Filename patterns tab, and add "*.m" again (it will already be there). The second "*.m" will be in your user database, which overrides anything in the system database.

I'll be adding this hack to the assoGiate manual in the next version.

---

### Post by mmendez on 2007-08-26
the easiest thing you could do without really changing anything is to do the following
```
sudo gedit /usr/share/mime/packages/freedesktop.org.xml
```

then search for "matlab" type Ctrl+f ...

then highlight everything from [COLOR="DeepSkyBlue"]<mime-type[/COLOR] [COLOR="SeaGreen"]type=[/COLOR][COLOR="Magenta"]"text/x-matlab"[/COLOR][COLOR="DeepSkyBlue"]>[/COLOR] on down to the first [COLOR="DeepSkyBlue"]</mime-type>[/COLOR] you see. it should be under the [COLOR="DeepSkyBlue"]<alias[/COLOR] [COLOR="SeaGreen"]type=[/COLOR][COLOR="Magenta"]"text/x-octave"[/COLOR]/[COLOR="DeepSkyBlue"]>[/COLOR]

Then just cut and paste this so that it is before the [COLOR="DeepSkyBlue"]<mime-type[/COLOR] [COLOR="SeaGreen"]type=[/COLOR][COLOR="Magenta"]"text/x-objcsrc"[/COLOR][COLOR="DeepSkyBlue"]>[/COLOR] that you can find by searching, I think it is only two mime-type entries above

because the [SIZE="4"]octave/matlab[/SIZE] entry is before the [SIZE="4"]object-c source code[/SIZE] entry that is what will be used first for anything and you should be good with that.

So then save it and go back to the command prompt and type ```
sudo update-mime-database /usr/share/mime/
```

and then just try it out with a test script or w/e

Manny

---

### Post by Wolki on 2007-08-26
> **mmendez said:**
> the easiest thing you could do without really changing anything is to do the following
```
sudo gedit /usr/share/mime/packages/freedesktop.org.xml
```


No, don't do that. Doing it like this will not only change it for all users (which may not be that bad if you're the only user, or if you want this change for all users) but since it directly edits a system file will be overwritten when that file is changed by ubuntu, so you'll have to do it again everytime the standard mime database is updated, and it's generally not a good idea.

Insted, declare the mime type again (i.e. copy the stuff regarding the matlab mime), either in the ~/.local/share/mime/packages/ (to change it for a single user) or "/usr/local/share/mime/packages/ (for a system-wide change).

If you want to really make sure, name the file Override.xml (or add the mime type definition to an already existing file with the same name). no matter, it should look similar to this:

```
<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns="http://www.freedesktop.org/standards/shared-mime-info">
  <mime-type type="text/x-matlab">
    <sub-class-of type="text/plain"/>
    <comment>MATLAB script/function</comment>
    <comment xml:lang="bg">&#1057;&#1082;&#1088;&#1080;&#1087;&#1090;/&#1092;&#1091;&#1085;&#1082;&#1094;&#1080;&#1103;, &#1092;&#1086;&#1088;&#1084;&#1072;&#1090; MATLAB</comment>
    <comment xml:lang="cs">Skript/funkce MATLAB</comment>
    <comment xml:lang="de">MATLAB-Skript/-Funktion</comment>
    <comment xml:lang="es">script/función de MATLAB</comment>
    <comment xml:lang="eu">MATLAB script/funtzioa</comment>
    <comment xml:lang="fi">MATLAB-skripti/funktio</comment>
    <comment xml:lang="fr">script/fonction MATLAB</comment>
    <comment xml:lang="hu">MATLAB parancsfájl/funkció</comment>
    <comment xml:lang="it">Script/Funzione MATLAB</comment>
    <comment xml:lang="ko">MATLAB &#49828;&#53356;&#47549;&#53944;/&#54632;&#49688;</comment>
    <comment xml:lang="nb">Skript/funksjon for MATLAB</comment>
    <comment xml:lang="nl">MATLAB-script/functie</comment>
    <comment xml:lang="nn">MATLAB skript/funksjon</comment>
    <comment xml:lang="pl">Skrypt/funkcja MATLABa</comment>
    <comment xml:lang="sv">MATLAB-skript/funktion</comment>
    <comment xml:lang="uk">&#1057;&#1094;&#1077;&#1085;&#1072;&#1088;&#1110;&#1081;/&#1092;&#1091;&#1085;&#1082;&#1094;&#1110;&#1103; MATLAB</comment>
    <comment xml:lang="vi">T&#7853;p l&#7879;nh/ch&#7913;c n&#259;ng MATLAB</comment>
    <magic priority="10">
      <match value="%" type="string" offset="0"/>
    </magic>
    <magic priority="50">
      <match value="function" type="string" offset="0"/>
    </magic>
    <glob pattern="*.m"/>
    <alias type="text/x-octave"/>
  </mime-type>
  <!-- more mime types may be defined here -->
</mime-info>
```

Then, run "update-mime-cache <directory>", where directory is the directory you put the file, minus the final "/packages". If you user the /usr/local" directory, you'll need to sudo that command.

This way, your changes should persist though updates to the standard database.

---

### Post by kdau on 2007-08-26
Actually, the other details (comment, alias, ...) for the MIME type shouldn't be copied to Override.xml, only the glob element for "*.m". A program like assoGiate automates this editing and updating process. If run with sudo, it will edit the file in /usr/local (for all users).

---

### Post by Wolki on 2007-08-26
> **kdau said:**
> Actually, the other details (comment, alias, ...) for the MIME type shouldn't be copied to Override.xml, only the glob element for "*.m". A program like assoGiate automates this editing and updating process. If run with sudo, it will edit the file in /usr/local (for all users).

You'e probably right, I just copy&pasted it from freedesktop.org.xml. I'll trust you as the expert. :)

---


---
title: "Mime types for custom file type"
date: 2012-07-31
forum: Desktop Environments
---

### Post by alexsb on 2012-07-31
I'm trying to register a custom file type as a mime-type in linux. My custom filetype, with a custom extension, is actually a zip archive containing various xml and other files. 

The problem I'm having is that my operating system (kubuntu) won't recognize the file as my custom mime-type but insists on it being a zip file. 

I'm not sure where I should start trying to fix my problem. I've used the following mime info file (tugraz-caleydo.sharedmimeinfo):
```

<?xml version="1.0" encoding="UTF-8"?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
<mime-type type="application/x-cal">  
<comment>Caleydo Project</comment>
<glob pattern="*.cal"/>
</mime-type>
</mime-info>

```

My Desktop Entry (caleydo.desktop, correctly registered in /usr/share/applications):
```

[Desktop Entry]
Version=2.01
Encoding=UTF-8
Name=Caleydo
GenericName=Data Visualization 
Comment=Visualization for Molecular Biology
Exec=/usr/bin/caleydo
Icon=/usr/share/pixmaps/caleydo_256.png
StartupNotify=true
Type=Application
Categories=Science;
MimeType=application/x-cal;

```

And these are the commands I'm trying to use:
```

sudo xdg-mime install --mode system tugraz-caleydo.sharedmimeinfo
sudo xdg-mime default caleydo.desktop application/x-cal
sudo update-mime-database /usr/share/mime

```

However, this still gives me:
```

$ xdg-mime query filetype export_2012.cal 
application/zip

```

---

### Post by alexsb on 2012-07-31
I finally found the issue:

the mime info file has to have exactly the name of the mime type. Renaming it to x-cal.xml did the trick.

---


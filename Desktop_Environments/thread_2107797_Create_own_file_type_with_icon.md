---
title: "Create own file type with icon"
date: 2013-01-22
forum: Desktop Environments
---

### Post by airglide on 2013-01-22
Hello everyone,

I've written a program which creates files named '*.not'. Now I would like to associate these files with my program. I've tried adding a mime type but with no effect. 

When I go to my file -> properties, there's written: (text/x-mup)

there should be (application/sourcenote or text/x-not)

I've read about a GUI which does that, but I want that to be done when a user installs my package. 

I've tried [https://help.ubuntu.com/community/AddingMimeTypes](https://help.ubuntu.com/community/AddingMimeTypes)

It would be great if someone could briefly summarize the steps or give me a helpful link ;)

thanks

airglide

---

### Post by airglide on 2013-01-26
I've solved my issue

I did the following: (I saw that *.not is already taken by another application so I changed to *.snot)

replace nameOfYourApp with the name of your application.

create **mimetype**: (for all users)
```

/usr/share/mime/packages

```place here a nameOfYourApp.xml which looks like:
```

<?xml version="1.0"?>
<mime-info xmlns='http://www.freedesktop.org/standards/shared-mime-info'>
  <mime-type type="application/nameOfYourApp">
    <comment>Sourcenote Textfile</comment>
    <generic-icon name="application-nameOfYourApp" />
    <glob pattern="*.snot"/>
  </mime-type>
</mime-info>

```replace *.snot with the ending you want 

to apply the changes update the mime database with:
```

sudo update-mime-database /usr/share/mime

```[B]
Icon[/B]

to add an Icon place it in: 
```

/usr/share/icons/hicolor/64x64/mimetypes/

```name of the file should be: application-nameOfYourApp.png

(your can also do this for different sizes replace the 64x64 with another size)

to update the icon cache type:

sudo gtk-update-icon-cache /usr/share/icons/hicolor

(you may want to add --force)

**set application to open specific type:**
add:
```
application-nameOfYourApp=nameOfYourApp.desktop
```to: 
```
/usr/share/applications/defaults.list
```maybe you nedd to add %U to exec = nameOfYourApp  in the file nameOfYourApp.desktop, this sign is filled with the files you want to open

the file should look like:

```

[Desktop Entry]
.. some lines of text
Exec=/usr/bin/SourceNote %U
MimeType=application/nameOfYourApp
... some lines of text

```the MimeType tells which files can be open by this application

If you would like to **change this only for one user,** look at:
```

~/.local/share/mime/packages/Override.xml

```update the mime-database (change the database: ~/.local/share/mime/)

```

~/.local/share/icons/hicolor/...

```and update the icons cache (change update location to ~/.local/share/icons/hicolor/)

If you have some additions let me know

airglide

---

### Post by dbruvers on 2013-10-22
Thank you for the very detailed information. Actually I only want to change the icon of PSD files but I think this will help me.

---

### Post by yanes on 2014-06-14
Or do all of this work in a few clicks using [URL="https://googledrive.com/host/0B9hT-mQsCjQZVU9sZHFWQmJxNzQ/"][I][B]Yanes-GMime  :) 


[ATTACH=CONFIG]253956[/ATTACH]
[/B][/I][/URL]
I hope it 'll help :)

---


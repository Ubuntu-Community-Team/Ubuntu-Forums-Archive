---
title: "Faulty MIME detection"
date: 2012-03-22
forum: Desktop Environments
---

### Post by tupfzom on 2012-03-22
Hi,

I'm working with MEI files, which are XML files. Unfortunately, they are detected as HTML. My problem: I'd rather have them open in the XML editor by default, and HTML files in the browser.

The smallest "legal" MEI file looks like
```

<?xml version="1.0"?>
<mei xmlns="http://www.music-encoding.org/ns/mei" meiversion="2012">
  <meiHead>
    <fileDesc>
      <titleStmt>
        <title/>
      </titleStmt>
      <pubStmt/>
    </fileDesc>
  </meiHead>
  <music/>
</mei>

```
xdg-mime tells me for this file:
```

$ xdg-mime query filetype mimeTest.mei 
text/html

```
My suspicion was that it might see the <title/> tag and for some strange reason think "ah, I know that, that's HTML". But for
```

<?xml version="1.0"?>
<mei xmlns="http://www.music-encoding.org/ns/mei" meiversion="2012">
  <meiHead>
    <fileDesc>
      <titleStmt/>
      <pubStmt/>
    </fileDesc>
  </meiHead>
  <music/>
</mei>
```
it still says
```

$ xdg-mime query filetype mimeTest.mei 
text/html
```
Only if I remove the <titleStmt/> entirely, it gives me
```

$ xdg-mime query filetype mimeTest.mei 
application/xml
```
As /etc/mime.types says:
> 
Users can add their own types if they wish by creating a ".mime.types" file in their home directory.

I created ~/.mime.types with content
```

application/xml			mei
```
But that didn't change anything.

Can anyone give me some advice on this?

---

### Post by LewisTM on 2012-03-22
First install package assogiate which provides the File Types Editor app (very handy).

Create a new type application/mei with Description 'MEI file'
In the Related types tab, add a parent type: application/xml
In the Filenames add *.mei
That's it. Now any file with .mei suffix will open with your XML editor and be called MEI file.
You can also experiment with detection by file contents if you want Ubuntu to find MEI files that don't have the .mei suffix.
The editor also allows your to specify a default icon so go ahead and choose your favorite music icon.

Cheers!

---

### Post by tupfzom on 2012-03-22
Thanks for the hint.  I added *.mei to the XML extensions with assogiate, no problems any longer.

The curious Linux user inside me is only wondering how this could have been done without dedicated software.

---

### Post by LewisTM on 2012-03-22
If you just wanted to add extensions (not create new types or change icons) I think you could have edited file ~/.local/share/mime/application/xml.xml
Or system-wide in /usr/share/mime/application/xml.xml
then ```
update-mime-database ~/.local/share/mime
```

---

### Post by tupfzom on 2012-03-22
I think I found some [background info on gnome.org]("http://library.gnome.org/admin/system-admin-guide/stable/mimetypes-database.html"). Thanks again.

---


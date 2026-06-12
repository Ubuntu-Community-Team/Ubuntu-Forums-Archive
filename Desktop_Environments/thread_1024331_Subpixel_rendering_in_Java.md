---
title: "Subpixel rendering in Java?"
date: 2008-12-28
forum: Desktop Environments
---

### Post by Munchkinguy on 2008-12-28
All of my Java applications look strange on my laptop because everything else has subpixel rendering, but the Java apps don't. How do I enable subpixel rendering for all Java applications in Ubuntu (Intrepid)?

---

### Post by Zorael on 2008-12-28
Don't Java programs read **~/.fonts.conf** for that? Make sure yours looks something like this. If you don't have one, create it.
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">

<fontconfig>
	<match target="font" >
		<edit mode="assign" name="embeddedbitmap">
			<bool>true</bool>
		</edit>
	</match>

	<match target="font" >
		<edit mode="assign" name="rgba">
			<const>rgb</const>
		</edit>
	</match>

        <match target="font" >
                <edit mode="assign" name="autohint">
                        <bool>false</bool>
                </edit>
        </match>

	<match target="font" >
		<edit mode="assign" name="hinting">
			<bool>true</bool>
		</edit>
	</match>

	<match target="font" >
		<edit mode="assign" name="hintstyle">
			<const>hintfull</const>
		</edit>
	</match>

	<match target="font" >
		<edit mode="assign" name="antialias">
			<bool>true</bool>
		</edit>
	</match>
</fontconfig>
```
You just need to close and reopen any applications to see the changes take effect.

---

### Post by Munchkinguy on 2008-12-29
That's a much handier way for configuring my QT applications, but it doesn't work for Java.

---

### Post by Zorael on 2008-12-30
Hmm. What of fontconfig, then?
```
$ sudo dpkg-reconfigure fontconfig-config
```
[list][*]Native
[*]Always
[*]Yes[/list]
```
$ sudo dpkg-reconfigure fontconfig
```

---

### Post by Munchkinguy on 2008-12-31
It's still the same.

---

### Post by Munchkinguy on 2009-01-02
I've been using Sun's proprietary Java but Freetype seems to have been implemented only in OpenJDK. So I'm going to install OpenJDK and see if there's any difference.

---

### Post by Munchkinguy on 2009-01-04
No, that didn't seem to work either.

---

### Post by benjabean1 on 2011-06-01
Bump

---


---
title: "Unable to set custom icon on application launcher"
date: 2011-01-19
forum: Desktop Environments
---

### Post by jaredhocutt on 2011-01-19
I am using Ubuntu 10.10 and having trouble setting a custom icon for an application launcher that I created. I have created and SVG file and placed it in **/usr/shared/icons/hicolor/scalable/apps/** and when I try to select it as the icon for the application launcher, it just goes back to the gnome-panel-launcher.svg default.

If I put the SVG file on my desktop and then select it, all is well. I'm assuming this is some type of permission problem, but I cannot seem to figure it out. I have set the permissions to be identical to the other icons in **/usr/shared/icons/hicolor/scalable/apps/**, but have no luck doing that either.

---

### Post by Krytarik on 2011-01-19
Personally I place custom icons in /usr/share/pixmaps and never had any problems with it, try those.

Greetings.

---

### Post by jaredhocutt on 2011-01-19
Thanks Krytarik.  It seems as though I can place the icon in any folder *other* than the /usr/share/icons/hicolor/ folder and it works.  So that solves my problem.

After doing some more research, I came across a comment that if an SVG file is placed in the /usr/shared/icons/hicolor/ folder, that a version for each size must be created as well.  I don't know if this is true, but may be helpful for anyone else who reads this thread.

---

### Post by Krytarik on 2011-01-19
> **jaredhocutt said:**
> 
After doing some more research, I came across a comment that if an SVG file is placed in the /usr/shared/icons/hicolor/ folder, that a version for each size must be created as well.  I don't know if this is true, but may be helpful for anyone else who reads this thread.
I expect that it's true, because all the icons are grouped in subfolders named by the size of the icons.

---

### Post by Andrew_P on 2012-02-12
> **jaredhocutt said:**
> After doing some more research, I came across a comment that if an SVG file is placed in the /usr/shared/icons/hicolor/ folder, that a version for each size must be created as well.  I don't know if this is true, but may be helpful for anyone else who reads this thread.

The full description of icon theme requirements can be found at the GNOME developer site:  [[COLOR="Blue"]_http://developer.gnome.org/icon-theme-spec/_[/COLOR]]("http://developer.gnome.org/icon-theme-spec/").

By experimenting, I find that putting an SVG version of the icon in /usr/share/icons/hicolor/scalable/apps *and* a PNG version of the icon in /usr/share/icons/hicolor/48x48/apps is sufficient to make the SVG version work in the Launcher.  In fact, the PNG version of the icon *doesn't even have to look like the SVG icon;* it can be *any* icon, as long as the base name of the PNG and SVG files are the same.  GNOME evidently uses the SVG version to create cached bitmap versions "on-the-fly" as it needs for the launcher, Main Menu and Applications Menu, ignoring the graphic content of the PNG version, even though it insists that a bitmap version exist in the /usr/icons/hicolor path.

This is one thing that Microsoft did much better in Windows 95 and later; Windows shortcuts are straightforward to create, and one can pick any icon file or icon from an icon library without restriction or having to go through contortions as one must with GNOME.  Unfortunately, the requirements for GNOME are not well documented where a novice can easily find them, and in many cases may require expertise with Inkscape and GIMP before one can create and maintain Launchers. ](*,)

---

### Post by Andrew_P on 2012-02-13
> **Krytarik said:**
> Personally I place custom icons in /usr/share/pixmaps and never had any problems with it, try those.

It doesn't work for SVG icons; I tried it. :(

If it worked for you, it's likely that at least one PNG version with the same base name already existed somewhere in the /usr/share/icons/hicolor path.  When I placed SVG, PNG and XPM versions of an icon into the /usr/share/pixmaps directory and made sure the /usr/share/hicolor path was completely devoid of an icon of the same base name, then tried to create a Launcher with the SVG icon, the icon image never appeared in the Main Menu — only a default rectangle showed.

---

### Post by Krytarik on 2012-02-13
> **Andrew_P said:**
> It doesn't work for SVG icons; I tried it. :(

If it worked for you, it's likely that at least one PNG version with the same base name already existed somewhere in the /usr/share/icons/hicolor path.
First, I was talking about *real* custom icons, not replacements!

Second, if you *do* replacements, don't narrow your focus solely on the "hicolor" icons, as it depends on what icon theme you are using what icon themes are crawled for a given icon name, in descending order, based on what's set to the "Inherits" key of the chosen icon theme, for example, this is from the default "Humanity" icon theme:

"/usr/share/icons/Humanity/index.theme":
```
[Icon Theme]
Name=Humanity
Comment=Smooth modern theme designed to be intuitive.
Inherits=gnome,hicolor
```But that doesn't apply to icons specified by an absolute path!

Lastly, SVG images for icons located in the "/usr/share/pixmaps" directory *do* work, I've just tested that with the "ubuntu-screensaver.svg", included there by default in my system (Lucid 10.04).

---

### Post by bovender on 2012-04-30
You must not use the .svg file extension in your .desktop file. Just enter the base file name of your SVG file, and it should work.

---


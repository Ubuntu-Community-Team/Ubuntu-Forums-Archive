---
title: "creating custom icons"
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by Irti on 2007-06-10
i already have a set of amazing icons which i downloaded while using xp.........the yare in the normal .png format.............is there any way i could build a custom icon theme using those icons....any help would be greatly appreciated.............

---

### Post by crimesaucer on 2007-06-10
I haven't tried to make my own Linux icons yet (i really like the Human themes)...but this is how I would try:

You could download an icon pack from Gnome-Looks, or take a look at your default Human icon pack, and then make your own icon pack with all of the exact icons needed, and put them in the exact same places as the Human icon theme pack does, with all of their exact sizes, and then just upload it to your /usr/share/icons (where your default Human icons are), and then select to use it from your User Interface Settings.

These are the folders in my Human_Effect_LightBlue icon pack that I'm using now.... the directory is located at: /usr/share/icons/Human_Effect_LightBlue in my xubuntu7.04 

You should have all of these different size directories:

Sizes are:
scalable
48x48
32x32
24x24
22x22
16x16
12x12
8x8

...and then most all of those folders should have more folders inside of them for: stock, status, places, mimetypse, filesystems, emblems, devices, categories, apps, actions...also

Inside of them will be all of the actual icon .pngs you will be making... 


--I've never tried this, but it should work, you will then have to move your new icon pack into your /usr/share/icons directory with your Terminal using sudo root privileges. 

To move it from your home directory into your /usr/share/icons directory, use this Terminal command:

```
sudo mv NEW_ICONS /usr/share/icons
```

...once again, I haven't done this, but this is how I would try to do it, since I basically do this when making my own gtk-2.0 themes.

........Now.....if you want to add new icons to your default Firefox Browser, they are located in this directory:

/usr/lib/firefox/chrome/classic/skin/classic/browser

and it is the Toolbar.png and it must be the default size of 336x120 (which is 24x24 for each icon), and they must be in the same order as the default classic theme which is like this:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Toolbar.png[/IMG]

I'm sure there is a userChrome.css to do this also, but I don't know what it is...

and last...if you would like to change your default icons in your Thunderbird 2 theme, then create a userChrome.css and add this in there:

```
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul");

/*toolbar icons*/
.toolbarbutton-1 {
  -moz-box-orient: vertical;
  list-style-image: url("mail-toolbar.png") !important;
}


```

and your icons should be put in the same /profile/chrome folder that your userChrome.css is in...also the default size is also 24x24 and the overall size is 408x72 and in this order...

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/mail-toolbar.png[/IMG]


...and this is what my Firefox and Thunderbird look like from doing my icons like that:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-120.png[/IMG]

---


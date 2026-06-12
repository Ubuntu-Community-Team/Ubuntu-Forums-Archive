---
title: "How can I change the icons used to display filetypes in a file manager"
date: 2019-12-01
forum: Desktop Environments
---

### Post by goemonburo on 2019-12-01
I recently switched to Arc theme (from default Lubuntu) and like it a lot, but noticed that none of my .iso files show as a disc icon anymore...instead, they show as a document, blurry, and I think it's because that's the default image when there's no other icon.  Not sure about that, but regardless, I'd love to edit that so that I can see a nice disc icon.

I tried looking at the .desktop files but that seems application-based.  Like if I wanted to change the VLC "construction cone" icon or something.  Which I don't.

I would like my file manager to show a disc icon whenever it's showing an .iso file.  Figure this can't be too hard but haven't figured it out yet.  

Thank you!

---

### Post by CatKiller on 2019-12-01
The icons that are shown for a given file type are determined by the icon theme. You can either look up the naming for your chosen icon from the freedesktop specification or just poke around with a theme that you know works. You just need icons of the right name in various sizes.

---

### Post by goemonburo on 2019-12-01
Thank you, @CatKiller, that's helpful.  So the theme I'm using, (Arc, in this case) doesn't have icons for a disk?  That seems odd but is there a way to find that specifically?  It's not hard to make icons, so I could manually do the graphics part.  But I don't know how to add them to the right place in the theme.

---

### Post by CatKiller on 2019-12-01
> **goemonburo said:**
> But I don't know how to add them to the right place in the theme.

Icon themes go in either /usr/share/icons (for system-wide themes) or ~/.local/share/icons (for per-user themes).

You don't necessarily need to create your own icon. If there's one you like you can just copy or symlink it to the theme you're using. Also, all themes inherit hicolor, so icons put in there will always be used if the theming system can't find one elsewhere.

---

### Post by goemonburo on 2019-12-01
Thank you again, @CatKiller.  But I am actually asking something different...obviously not explaining it well.  

What specifically do I symlink FROM to get an icon, call it /some/path/to/the/icon.png to show up as the icon when I am using the file manager?  

I understand the locations.  But it seems like there's some file, call it, "default-cd-icon.png" that I need to add, change, create, or replace to make this work.

Currently it seems my theme doesn't include that icon.  So I can't symlink to a different one if it doesn't have one to start with.

If I go to /usr/share/icons there are a dozen different folders, each for a specific theme.  Inside those folders are more folders.  If I want /some/path/to/the/icon.png to be the icon that's used, which folder do I use?  In my "/usr/share/icons/Tango/scalable/devices" folder there are a number of cd-like icons I can use.  But I don't know where to link that.  I suspect I have to find some file that defines a ".iso" filetype, and change that file to point to /some/path/to/the/icon.png.  No?  If so...how do I do that.  :-)  

I hope that makes more sense?

---

### Post by Dennis N on 2019-12-01
The file type icons are derived from the mime type of the file.

Get mime type of .iso file by right click  > Properties. Look for MIME type. The iso files are probably using MIME type **application/x-cd-image**.

Look at mimetypes folder in your theme folder to locate the image file for this mime type. My icon theme is Paper:

```
dmn@Tyana-vm:/usr/share/icons/Paper/48x48/mimetypes$ ls | grep x-cd-image
application-x-cd-image.png

```
This matching .png is what is providing the image. It may exist in various sizes. You can check folders for other icon sizes and scalable (if it exists) as well. Some sizes (like 32x32) won't have an icon. An algorithm selects the best size for the icon from what sizes are available. You could substitute an icon from another theme, or resize an existing size to provide a missing size.

Note: I used Lubuntu 19.10 for the above information and output

---

### Post by CatKiller on 2019-12-01
> **goemonburo said:**
> Thank you again, @CatKiller.  But I am actually asking something different...obviously not explaining it well.  

What specifically do I symlink FROM to get an icon, call it /some/path/to/the/icon.png to show up as the icon when I am using the file manager?   

From whichever theme you were using before, or whichever other theme you like that does provide an icon. That's why I said you should have a look at the other themes to see how it works. 

>  I understand the locations.  But it seems like there's some file, call it, "default-cd-icon.png" that I need to add, change, create, or replace to make this work. 

That's right. 

>  Currently it seems my theme doesn't include that icon.  So I can't symlink to a different one if it doesn't have one to start with. 

Your symlink in that theme would be to the equivalent location in a different theme. Or copied from the other theme. So when the theming system requests the icon, there's one there. 

>  If I go to /usr/share/icons there are a dozen different folders, each for a specific theme.  Inside those folders are more folders.   

That's right. Some themes are organised by type then size, some are organised by size then type. The index.theme file specifies how a particular theme is laid out. 

>  If I want /some/path/to/the/icon.png to be the icon that's used, which folder do I use?  In my "/usr/share/icons/Tango/scalable/devices" folder there are a number of cd-like icons I can use.  But I don't know where to link that.  I suspect I have to find some file that defines a ".iso" filetype, and change that file to point to /some/path/to/the/icon.png.  No?  If so...how do I do that.  :-)   

No. The filename is already defined. That's all that matters. You don't need to change anything else, just provide a file of the correct name in the directories that your theme is looking in. There is a [specification](https://specifications.freedesktop.org/icon-theme-spec/icon-theme-spec-latest.html) that lays out how the icon is retrieved, but it's terribly dull, so it's just way easier, and way quicker, to simply look at a theme you know works to see what the filename should be.

Say you've got a launcher for Thunderbird, for example. All that needs to include is "Icon=thunderbird" and it's done. No messing about with hard-coded paths or file extensions; the correct icon at the correct size for your theme can be automatically picked just from that, and if your theme doesn't have an icon one can be chosen from the stylistically-similar ones specified in the Inherits for the theme, all the way back to hicolor. When you change theme, all the icons can just change together.

I don't know the icon name for your MIME type, although Dennis N has pointed the way, and I'm typing from my phone so I can't check for you. You'll find it, I'm sure.

---

### Post by goemonburo on 2019-12-01
@Dennis N, this was exactly what I needed.  Thank you.  

So when I right click and check properties, I don't get anything that says MIME type.  I do have a line that says "file type" and it's "raw cd image."  So how do I sleuth out the location of that image?

Thank you again.

For CatKiller, I still don't understand how to determine the "correct name in the directories [my] theme is looking in."  I'll mess around a bit and see if I stumble onto it.  And yeah, sorry, phones aren't the best for that stuff.  Thank you just the same for trying to help!  I appreciate it!!

---

### Post by goemonburo on 2019-12-01
Some further fiddling, I've gotten the INDIVIDUAL icon to change by right-clicking on the file, then going to Properties, then double clicking the icon, and selecting a different icon.  (Only works in Nautilus.  My main file manager, PCManFM, doesn't have that).  Problem is I don't want to do this for each of my gazillion .iso files.

---

### Post by CatKiller on 2019-12-02
> **goemonburo said:**
> 
For CatKiller, I still don't understand how to determine the "correct name in the directories [my] theme is looking in."  I'll mess around a bit and see if I stumble onto it.

That's exactly how you do it ;)

You know that whichever theme you were using before (or the theme that theme inherits) definitely includes an icon for that filetype (since you noticed its absence when you switched themes). That theme is either going to be structured as theme/<sizes>/<category> or theme/<category>/<sizes>. The category you're interested in is going to be called something like mimetypes or mimes; those names *aren't* fixed, they're whatever made sense to the person that made the theme. The file is likely to be called something like application-x-cd-image.

Once you've identified the files (there'll be one for each size the theme provides) you can copy or symlink them into the structure of your new theme. Or, if that icon doesn't fit into the style of your new theme, find an icon that does, either online, or in a different theme, or wherever.

There's a command that I can't remember for reloading all of the theme's icons once you've put the new files in, but logging out and logging back in will probably do the same thing.

---

### Post by goemonburo on 2019-12-02
@CatKiller, thank you again -- that's much clearer and essentially what I thought needed to happen.  But now the mystery:  in the icon theme I THINK I'm using (Arc, at least when I see it in Gnome-Tweaks), there already ARE icons that have "application-x-cd-image.png."  

So with icons already there...why aren't they showing up?!  Is there some additional step I'm missing?  Is it the fact that I've changed the default program they're opened with from whatever it was to VLC and there's no corresponding VLC icon in this theme???  Could that be it?

---

### Post by CatKiller on 2019-12-02
> **goemonburo said:**
> So with icons already there...why aren't they showing up?! 
No idea. I don't use Lubuntu and I don't use Arc. As far as I can tell, Arc's icon for the cd image MIME type should look like [this](https://github.com/horst3180/arc-icon-theme/blob/master/Arc/mimetypes/128/application-x-cd-image.png). Is that what you see? That *could* look like a "blurry document" at some sizes, I'd imagine. Or you could be using something that isn't Arc. 

You can always copy the icon theme's directories to the appropriate place in your Home folder and change any icons that you don't like. Per-user themes override system themes and don't get changed by upgrades.

Changing the default application through the file browser wouldn't have affected anything, but I suppose it's possible that VLC messed with the MIME database in some way to lay claim to those files if you did it through VLC. It shouldn't have, but applications can always do the wrong thing and Windows, where messing with the MIME database could well be an appropriate action, is VLC's primary development target.

Potentially relevant: from the Arc readme 
> This theme doesn't provide application icons, it needs another icon theme to inherit them. By default this theme will look for the Moka icon theme to get the missing icons. If Moka is not installed it will use the Gnome icon theme as fallback. To change the application icons, edit Arc/index.theme and replace Moka with the name of your preferred icon theme
so the Arc devs suggest using Moka to fill in any gaps in what their own theme provides.

---

### Post by Dennis N on 2019-12-02
> **goemonburo said:**
> @Dennis N, this was exactly what I needed.  Thank you.  
So when I right click and check properties, I don't get anything that says MIME type.  I do have a line that says "file type" and it's "raw cd image."  So how do I sleuth out the location of that image?
I installed Arc Icon Theme from gnome-look.org on Lubuntu 19.10 to check it out. I attached the Properties window from an .iso file. Mine shows the MIME type. Also, notice there is a preview of the icon for the file in the upper left (a disk), and that's what shows in my PCManFM file manager as well (2nd screenshot). You don't you get that?

If not, I suggest you re-acquire the icon theme and replace the existing set.

---

### Post by goemonburo on 2019-12-02
[ATTACH=CONFIG]284538[/ATTACH]

So this is what I'm getting for my .iso file.  And if I right click and choose properties, it's this:

[ATTACH=CONFIG]284539[/ATTACH]

I've read the process for changing themes and it seems straightforward:  put it in your .themes or .icons folder, use "gnome-tweaks" (or Unity-tweak-tool?) to select it.  Log out, log in...voila.

No?

If I go into the theme, I can see that same image (white page with "cd" circles) in all the various sizes and folders.  

Pulling my hair out at this point.  It's not even that important, so I may just live with it, but ideally, it just seems like something that should be easy to identify and fix.  Right?  :-)

---

### Post by goemonburo on 2019-12-02
Also, just in case it isn't obvious -- the mp4 file is just there as an example of one that's working.  Most of the other file types seem to be fine, like spreadsheets, text documents, audio and so on...

---

### Post by goemonburo on 2019-12-02
Okay, I believe that I've gotten somewhere:

1)  By going through and looking at the icons I've got showing, they appear identical to Adwaita's, NOT Arc, as I'd hoped.
2)  Yet when I use gnome-tweaks to choose, I see that Arc is showing up in both the Theme and Icon options.  

Does this get me any further??

---

### Post by CatKiller on 2019-12-02
Well, you know how to add extra icons to Adwaita now.

Other desktop environments aren't as limited as Gnome; they don't need a helper application just to set preferences. You aren't using Gnome, so there's no point in using gnome-tweak. Set your theme in your normal Preferences/Customisation area.

---

### Post by Dennis N on 2019-12-02
> I've read the process for changing themes and it seems straightforward: put it in your .themes or .icons folder, use "gnome-tweaks" (or Unity-tweak-tool?) to select it. Log out, log in...voila.

No?

Tell us what version of Lubuntu you are using. What I have posted came from Lubuntu 19.10. Also from your post #9, it seems you are using multiple file managers? Don't install gnome tweaks tool, as that will also install gnome desktop environment! When you stray from a standard Lubuntu install (like I am using) by adding other file managers or additional desktop environments, I can't predict what effects that will have. Sorry.[U]

Other comments:[/U]
There is no Arc icon theme in the repositories, so you must have downloaded it as an archive file from someplace else? In Lubuntu, changing to the downloaded theme is simple. Just extract the theme folder from the archive, and copy it to one of:

/usr/share/icons
~/.local/share/icons
~/.icons 

It should then be available for selection.

Select icon theme from: **Menu > Preferences > LXQt Settings > Appearance > Icons Theme**
Once selected in this dialog, click "Apply" and it should update the theme instantly.

---

### Post by goemonburo on 2019-12-02
Solved.  @CatKiller, you get the bonus points, though I wish we'd started with that original suggestion:  change the theme in that Preferences > Customize Look and Feel.  That's what I needed.  Chose "Arc" and instantly all was good in the hood.  I had a feeling it was actually that easy.  Just had to use that tool rather than gnome-tweaks or unity-tweak-tool.

I'm seeing what I should be now.  Whew!

---


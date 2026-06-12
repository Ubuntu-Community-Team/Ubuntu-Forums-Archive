---
title: "firefox shockwave player v.s. flash player"
date: 2009-04-17
forum: General Help
---

### Post by banana jama on 2009-04-17
i've recently downloaded Ubuntu 9.04 RC and when using Firefox was notified to downloaded the Shock wave player when looking at videos on youtube. is there a difference between the shock wave player and adobe flash 10. I've notice that i can't watch videos on Hulu, Charlie rose.com, among other websites. when i try to download the flash player on adobe's website it isn't added to my add-ons. also when i go to the shock wave player website it says "this platform is not supported". how do i get rid of shockwave and replace it with flash player 10.

---

### Post by codeseer on 2009-04-17
64-bit?

---

### Post by mb_webguy on 2009-04-17
You can install Flash by installing either the flashplugin-nonfree or ubuntu-restricted-extras package.  The latter will install the former and a few other things besides.

Shockwave is an older, rarely used technology, which was replaced by Flash.  Adobe never released a Shockwave plugin for Linux, and since it's an older technology it's unlikely they ever will.  Since there's little demand for a Shockwave plugin, it's unlikely an open-source plugin will ever be developed, either.  If you absolutely must have Shockwave for some website, you'll have to install the Shockwave plugin on the Windows version of Firefox under Wine.

I don't know why YouTube or Hulu would be asking you to install the Shockwave plugin, however, since both use Flash, and not Shockwave.

---

### Post by EnglishSparrow on 2009-04-17
Both websites you say use flash. You can remove the program with synaptic.

As for hulu saying that this platform is not supported, they mean Linux is not supported. I got around this by running firefox in wine.

---

### Post by codeseer on 2009-04-17
> **mb_webguy said:**
> You can install Flash by installing either the flashplugin-nonfree or ubuntu-restricted-extras package.  The latter will install the former and a few other things besides.

Shockwave is an older, rarely used technology, which was replaced by Flash.  Adobe never released a Shockwave plugin for Linux, and since it's an older technology it's unlikely they ever will.  Since there's little demand for a Shockwave plugin, it's unlikely an open-source plugin will ever be developed, either.  If you absolutely must have Shockwave for some website, you'll have to install the Shockwave plugin on the Windows version of Firefox under Wine.

I don't know why YouTube or Hulu would be asking you to install the Shockwave plugin, however, since both use Flash, and not Shockwave.

The new Flash plugin is called "Shockwave Flash" for Linux. That flashplugin-nonfree, or teatime whatever stuff, doesn't work on all the video sites. You have to get the official one.

Here's the instructions I wrote for myself when I had to deal with the mess:

```

Download it from here: http://labs.adobe.com/downloads/flashplayer10.html

Extract it using: tar zxvf libflashplayer-*.tar.gz

Clean up past installation of Flash:

sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

Install the new Flash:

sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/
sudo ln -sf /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/xulrunner-addons/plugins

```

Edit:

You have to disable that 'tea whatever' plugin if it's in your Firefox plugins list. I forget the name of it.

This will get Hulu, YouTube, SouthParkStudios, etc to work.  What will still not work is the sites that use a proprietary player like the 'Move Player'; to name a couple ABC and CW. These won't even work in Wine or a VirtualBox, because evidently they have to hook to the video card for DRM junk.

---

### Post by banana jama on 2009-04-17
codeseer theres only a 64bit option im using a 32-bit os.

Edit: never mind thanks codeseer i install flash ten from adobe's website then i used the sudo rm commands from your previous comment to remove the previous shock wave flash for linux. everything works now (hulu, youtube,etc.) thanks alot fot the assistance.

---

### Post by codeseer on 2009-04-17
> **banana jama said:**
> codeseer theres only a 64bit option im using a 32-bit os.

:/

Well, I think you have to get the 64-bit download then wrap it and plug it like the instructions say. Let me see if I can dig up a how-to on that.

Edit:

This is basically how to do it:
[http://www.hildoersystems.com/index.php?option=com_content&view=article&id=76:adobe-flash-10-for-ubuntu-desktop-32bit-and-64bit&catid=39:multimedia&Itemid=59]("http://www.hildoersystems.com/index.php?option=com_content&view=article&id=76:adobe-flash-10-for-ubuntu-desktop-32bit-and-64bit&catid=39:multimedia&Itemid=59")

You have to wrap the 64-bit, which makes it compatible with Firefox 32-bit.

---

### Post by codeseer on 2009-04-17
On second look, they evidently have a package for it now:

[http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb")

See if that works.

Edit:

Oh, I see your edit now from the previous post. Great! Glad to help.

---

### Post by Niksko on 2009-06-23
Thank you soooo much codeseer. Your instructions helped get things working nicely for me after I had issues. I moved over to Jaunty and I was prompted upon visiting youtube to install a missing plugin. There were three options (which I can't remember) for installing a flash plugin, and I just picked one at random thinking it would make no difference. All flash players became rather broken and the audio would often squeak like when you listen to voices in fast forward. Your instructions helped to fix things entirely.

Thanks again

-Nik

---

### Post by fmurrieta on 2009-09-07
Thank you, thank you codeseer

I've used your instructions to uninstall all previous mess I've done.

After that I've used macromedia's deb as you suggested, everything worked like a charm!

Thank you all

Long live ubuntu!

---

### Post by hopeididgood on 2009-09-08
Just another thank you to codeseer.  This issue has been driving me crazy; these instructions worked perfectly!

---


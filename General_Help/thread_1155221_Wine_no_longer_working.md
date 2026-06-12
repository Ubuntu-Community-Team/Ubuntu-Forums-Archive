---
title: "Wine no longer working"
date: 2009-05-10
forum: General Help
---

### Post by afrodeity on 2009-05-10
Wine is no longer working in Ubuntu Hardy. This could be something to do with the recent update to kernal 24-24. Virtualbox for instance, needed to recompile itself in order to work. Is there a solution for Wine?

---

### Post by gradysghost on 2009-05-10
It works for me.  You can run through [this excellent guide]("http://www.winehq.org/download/deb"), straight from the Wine guys themselves, which shows how to convince Ubuntu to use the most recent stable version.  I haven't had any trouble with it in Hardy, Intrepid, or Jaunty.  Good luck!

---

### Post by afrodeity on 2009-05-10
Or it could be a regression? I've updated the repository with the beta wine details and the system appears to be updating and installing a newer version. Will wait and see if this fixes anything.

UPDATE: It installed. I rebooted, but nothing. Wine is definitely not working, even the newer version.

---

### Post by afrodeity on 2009-05-11
That would be wine-1.1.21 on Ubuntu 8.04.2, kernel 2.6.24-24

-- please somebody help

UPDATE: I tried booting with the 24-23 kernel, but still nothing. Must be the  application!

---

### Post by afrodeity on 2009-05-19
I ran winecfg in terminal and here is what I get:

```

afrodeity@afrodeity-desktop:~$ winecfg
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
fixme:advapi:RegisterEventSourceW ((null),L"Bonjour Service"): stub
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WS_setsockopt Unknown level: 0x00000029
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:winsock:WSAIoctl -> SIO_ADDRESS_LIST_CHANGE request: stub
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:iphlpapi:GetAdaptersAddresses no support for IPv6 addresses
fixme:winsock:WS_setsockopt Unknown IPPROTO_IP optname 0x00000013
fixme:winsock:WSAIoctl SIO_GET_EXTENSION_FUNCTION_POINTER {f689d7c8-6f1f-436b-8a53-e54fe351c322}: stub
fixme:service:EnumServicesStatusW 0x1183e8 type=30 state=3 (nil) 0 0x87e7b8 0x87e7c4 0x87e7c0
fixme:advapi:ReportEventA (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x87e5c8,(nil)): stub
fixme:advapi:ReportEventW (0xcafe4242,0x0004,0x0000,0x20000001,(nil),0x0001,0x00000000,0x118218,(nil)): stub
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
Wine cannot find the FreeType font library.  To enable Wine to
use TrueType fonts please install a version of FreeType greater than
or equal to 2.0.5.
http://www.freetype.org
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"winex11.drv": libXext.so.6: cannot open shared object file: No such file or directory
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
Application tried to create a window, but no driver could be loaded.
Unknown error (127).
err:ole:apartment_createwindowifneeded CreateWindow failed with error 127
afrodeity@afrodeity-desktop:~$ 

```

Something to do with Freetype/Truetype fonts. Any advice and how to go about rectifying this tragic situation?

---

### Post by Legace on 2009-05-19
Try to install/reinstall ttf-mscorefonts-installer

---

### Post by afrodeity on 2009-05-19
There is a general linux tutorial here [http://www.cyberciti.biz/tips/linux-howto-install-truetype-freetype-and-msttcorefonts-fonts.html](http://www.cyberciti.biz/tips/linux-howto-install-truetype-freetype-and-msttcorefonts-fonts.html)
but I can't seem to find the /etc/X11/XF86Config-4 file which apparently needs to be edited. Is there a different set-up of Freetype in Ubuntu Hardy?

---

### Post by afrodeity on 2009-05-19
```

afrodeity@afrodeity-desktop:~$ sudo apt-get install ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ttf-mscorefonts-installer
afrodeity@afrodeity-desktop:~$ 

```

Could be bandwidth issue, but it should be in the local repository, surely? Is there a source I need to add for this?

UPDATE: [http://packages.ubuntu.com/jaunty/all/ttf-mscorefonts-installer/download](http://packages.ubuntu.com/jaunty/all/ttf-mscorefonts-installer/download)
downloaded it but can't install because of bandwidth issue

---

### Post by afrodeity on 2009-05-23
I managed to install msstcorefonts, but no solve the problem. The seperate installer won't work because of bandwidth. I've downloaded the freetype fonts but not sure how to proceed from here. Any help?

UPDATE: separate installer just installs msstcorefont alternatives. Not solved the problem.

---

### Post by afrodeity on 2009-06-01
```
dpkg-reconfigure x-ttcidfont-conf
```

which gives a drop down menu to select truetype/freetype fonts

Now I am a bit baffled by the [instructions]("http://www.cyberciti.biz/tips/linux-howto-install-truetype-freetype-and-msttcorefonts-fonts.html") which are for Debian.

```
Open /etc/X11/XF86Config-4 file and append following FontPath:
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
```

all I can find is  XvMCConfig which I edited as above

then

```
Open XFS /etc/X11/fs/config file
# vi /etc/X11/fs/config

Append above font paths catalogue option, which specifies paths to search for fonts. At the end, your entry should look like as follows:
catalogue = /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/,/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID/,/usr/lib/X11/fonts/misc/,/usr/lib/X11/fonts/cyrillic/,/usr/lib/X11/fonts/100dpi/:unscaled,/usr/lib/X11/fonts/75dpi/:unscaled,/usr/lib/X11/fonts/Type1/,/usr/lib/X11/fonts/CID,/usr/lib/X11/fonts/Speedo/,/usr/lib/X11/fonts/100dpi/,/usr/lib/X11/fonts/75dpi/


```
I can't find /etc/X11/fs/config in Ubuntu, maybe its called something else? 

Close and save the file. Restart the system:
# reboot

 Freetype is also available here [http://freetype.sourceforge.net/download.html#stable](http://freetype.sourceforge.net/download.html#stable)

---

### Post by afrodeity on 2009-06-01
```
afrodeity@afrodeity-desktop:~$ dpkg -l "*freetype*"
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  freetype       <none>         (no description available)
un  freetype0      <none>         (no description available)
un  freetype0-dev  <none>         (no description available)
un  freetype1      <none>         (no description available)
un  freetype1-dev  <none>         (no description available)
ii  libfreetype6   2.3.5-1ubuntu4 FreeType 2 font engine, shared library files
ii  libfreetype6-d 2.3.5-1ubuntu4 FreeType 2 font engine, development files
afrodeity@afrodeity-desktop:~$ 

```

I tried using the ttf-msstcorefonts alternative, but no luck. Stumped.

---

### Post by afrodeity on 2009-06-01
```
sudo apt-get build-dep wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/www.salatti.net_repo_dists_hardy-salatti_main_source_Sources - open (2 No such file or directory)
afrodeity@afrodeity-desktop:~/Desktop$ 

```

---

### Post by afrodeity on 2009-06-03
Installed Freetype manually but Wine can't find the fonts. How do I get Wine to recognise them? Symbolic links probably needed, but where?

---

### Post by sydbat on 2009-06-10
To revive this thread...

I was having the same problem after the last beta upgrade (1.1.23). Uninstalled completely, removed /.wine folder, reinstalled, configured, and it still did not work. Followed the link in the first response ([http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)) and grabbed the previous version I knew worked (1.1.22) and did a clean install with that.

Problem solved.

Now I will submit a bug letting them know.

---

### Post by afrodeity on 2009-06-10
Thanks for letting me know. I was going mad trying to figure out why ia32-libs giving me hassles trying to compile WINE with FREETYPE, so it's definitely a bug. Will see if I can revert.

---

### Post by afrodeity on 2009-06-19
I tried deleting the .wine folder and installing 1.1.22. No go. I am now back with the original Wine package that comes with Ubuntu repos, 1.0.0, and still the bloody problem with Freetype. How can I remove this obstacle? Is it some plot by Codeweavers to force us to buy a commercial version of WINE?

---

### Post by afrodeity on 2009-06-19
I did a locate for Freetype,

```
/usr/share/doc/libfreetype6/CHANGES.gz
/usr/share/doc/libfreetype6/CUSTOMIZE.gz
/usr/share/doc/libfreetype6/ChangeLog.gz
/usr/share/doc/libfreetype6/DEBUG.gz
/usr/share/doc/libfreetype6/FTL.TXT.gz
/usr/share/doc/libfreetype6/GPL.TXT.gz
/usr/share/doc/libfreetype6/INSTALL
/usr/share/doc/libfreetype6/INSTALL.ANY.gz
/usr/share/doc/libfreetype6/INSTALL.CROSS.gz
/usr/share/doc/libfreetype6/INSTALL.GNU.gz
/usr/share/doc/libfreetype6/INSTALL.MAC
/usr/share/doc/libfreetype6/INSTALL.UNIX
/usr/share/doc/libfreetype6/INSTALL.VMS
/usr/share/doc/libfreetype6/LICENSE.TXT
/usr/share/doc/libfreetype6/MAKEPP
/usr/share/doc/libfreetype6/PATENTS
/usr/share/doc/libfreetype6/PROBLEMS
/usr/share/doc/libfreetype6/README.Debian
/usr/share/doc/libfreetype6/TODO
/usr/share/doc/libfreetype6/TRUETYPE
/usr/share/doc/libfreetype6/UPGRADE.UNIX.gz
/usr/share/doc/libfreetype6/VERSION.DLL.gz
/usr/share/doc/libfreetype6/changelog.Debian.gz
/usr/share/doc/libfreetype6/changelog.gz
/usr/share/doc/libfreetype6/copyright
/usr/share/doc/libfreetype6/design
/usr/share/doc/libfreetype6/formats.txt.gz
/usr/share/doc/libfreetype6/ft2faq.html
/usr/share/doc/libfreetype6/glyphs
/usr/share/doc/libfreetype6/pcf
/usr/share/doc/libfreetype6/raster.txt.gz
/usr/share/doc/libfreetype6/reference
/usr/share/doc/libfreetype6/release.gz
/usr/share/doc/libfreetype6/tutorial
/usr/share/doc/libfreetype6/design/basic-design.png
/usr/share/doc/libfreetype6/design/design-1.html
/usr/share/doc/libfreetype6/design/design-2.html
/usr/share/doc/libfreetype6/design/design-3.html
/usr/share/doc/libfreetype6/design/design-4.html
/usr/share/doc/libfreetype6/design/design-5.html
/usr/share/doc/libfreetype6/design/design-6.html
/usr/share/doc/libfreetype6/design/detailed-design.png
/usr/share/doc/libfreetype6/design/index.html
/usr/share/doc/libfreetype6/design/library-model.png
/usr/share/doc/libfreetype6/design/simple-model.png
/usr/share/doc/libfreetype6/glyphs/Image1.png
/usr/share/doc/libfreetype6/glyphs/Image2.png
/usr/share/doc/libfreetype6/glyphs/Image3.png
/usr/share/doc/libfreetype6/glyphs/Image4.png
/usr/share/doc/libfreetype6/glyphs/bbox1.png
/usr/share/doc/libfreetype6/glyphs/bbox2.png
/usr/share/doc/libfreetype6/glyphs/body_comparison.png
/usr/share/doc/libfreetype6/glyphs/bravo_kerned.png
/usr/share/doc/libfreetype6/glyphs/bravo_unkerned.png
/usr/share/doc/libfreetype6/glyphs/clipping.png
/usr/share/doc/libfreetype6/glyphs/down_flow.png
/usr/share/doc/libfreetype6/glyphs/glyphs-1.html
/usr/share/doc/libfreetype6/glyphs/glyphs-2.html
/usr/share/doc/libfreetype6/glyphs/glyphs-3.html
/usr/share/doc/libfreetype6/glyphs/glyphs-4.html
/usr/share/doc/libfreetype6/glyphs/glyphs-5.html
/usr/share/doc/libfreetype6/glyphs/glyphs-6.html
/usr/share/doc/libfreetype6/glyphs/glyphs-7.html
/usr/share/doc/libfreetype6/glyphs/grid_1.png
/usr/share/doc/libfreetype6/glyphs/index.html
/usr/share/doc/libfreetype6/glyphs/points_conic.png
/usr/share/doc/libfreetype6/glyphs/points_conic2.png
/usr/share/doc/libfreetype6/glyphs/points_cubic.png
/usr/share/doc/libfreetype6/glyphs/points_segment.png
/usr/share/doc/libfreetype6/glyphs/twlewis1.png
/usr/share/doc/libfreetype6/glyphs/twlewis2.png
/usr/share/doc/libfreetype6/glyphs/up_flow.png
/usr/share/doc/libfreetype6/pcf/README
/usr/share/doc/libfreetype6/reference/ft2-base_interface.html
/usr/share/doc/libfreetype6/reference/ft2-basic_types.html
/usr/share/doc/libfreetype6/reference/ft2-bdf_fonts.html
/usr/share/doc/libfreetype6/reference/ft2-bitmap_handling.html
/usr/share/doc/libfreetype6/reference/ft2-cache_subsystem.html
/usr/share/doc/libfreetype6/reference/ft2-computations.html
/usr/share/doc/libfreetype6/reference/ft2-font_formats.html
/usr/share/doc/libfreetype6/reference/ft2-gasp_table.html
/usr/share/doc/libfreetype6/reference/ft2-glyph_management.html
/usr/share/doc/libfreetype6/reference/ft2-glyph_stroker.html
/usr/share/doc/libfreetype6/reference/ft2-gx_validation.html
/usr/share/doc/libfreetype6/reference/ft2-gzip.html
/usr/share/doc/libfreetype6/reference/ft2-header_file_macros.html
/usr/share/doc/libfreetype6/reference/ft2-incremental.html
/usr/share/doc/libfreetype6/reference/ft2-index.html
/usr/share/doc/libfreetype6/reference/ft2-lcd_filtering.html
/usr/share/doc/libfreetype6/reference/ft2-list_processing.html
/usr/share/doc/libfreetype6/reference/ft2-lzw.html
/usr/share/doc/libfreetype6/reference/ft2-mac_specific.html
/usr/share/doc/libfreetype6/reference/ft2-module_management.html
/usr/share/doc/libfreetype6/reference/ft2-multiple_masters.html
/usr/share/doc/libfreetype6/reference/ft2-ot_validation.html
/usr/share/doc/libfreetype6/reference/ft2-outline_processing.html
/usr/share/doc/libfreetype6/reference/ft2-pfr_fonts.html
/usr/share/doc/libfreetype6/reference/ft2-raster.html
/usr/share/doc/libfreetype6/reference/ft2-sfnt_names.html
/usr/share/doc/libfreetype6/reference/ft2-sizes_management.html
/usr/share/doc/libfreetype6/reference/ft2-system_interface.html
/usr/share/doc/libfreetype6/reference/ft2-toc.html
/usr/share/doc/libfreetype6/reference/ft2-truetype_engine.html
/usr/share/doc/libfreetype6/reference/ft2-truetype_tables.html
/usr/share/doc/libfreetype6/reference/ft2-type1_tables.html
/usr/share/doc/libfreetype6/reference/ft2-user_allocation.html
/usr/share/doc/libfreetype6/reference/ft2-version.html
/usr/share/doc/libfreetype6/reference/ft2-winfnt_fonts.html
/usr/share/doc/libfreetype6/tutorial/example1.c
/usr/share/doc/libfreetype6/tutorial/metrics.png
/usr/share/doc/libfreetype6/tutorial/metrics2.png
/usr/share/doc/libfreetype6/tutorial/step1.html
/usr/share/doc/libfreetype6/tutorial/step2.html

```

---

### Post by wandalalakers on 2009-06-19
The program winedevice.exe has caused a serious problem and needs to close. We are sorry for the inconvience.
I'm running Macromedia Flash 8 when this error occurs.
I'm also unable to run the "Uninstall Wine Software" program.
When I click it, nothing happens.
This happens with wine 1.1.22 and 1.1.23. I posted this error message on the wine forum today but for some reason I couldn't login anymore after posting my wine error message on their forum.  I'm using kubuntu 8.04 by the way.  I ended up removing 1.1.23 and reinstalled 1.1.19.

[http://forum.winehq.org/viewtopic.php?t=5257](http://forum.winehq.org/viewtopic.php?t=5257)

---


---
title: "Problems with UT2004 sound sluggish"
date: 2005-12-31
forum: Gaming &amp; Leisure
---

### Post by jimchristopher on 2005-12-31
I am somewhat of a linux newb, not a PC newb.  I recently installed ubuntu and after some initial ATI problems and swapping out for a nv 6600GT I got accellerated 3D and tried some games.  I installed UT2004 and although it starts up fine and I have sound it is extremely slow sounding, reeeaaaalllly sllllooooowww.

I am using ubuntu 5.10 on a shuttle SN25P small form factor system.  there are no PCI slots, and onboard Envy24 sound.  I have tried several hacks for recompiling alsa sound, I got it to break to where I had NO sound, then got it back up with the same issues.  I also tried a kernel compiling for newbs thread by tseliot, that hasnt worked.  I see that there is support for this chip and I compiled it into the kernel as far as i can tell.  

Can anyone help get my sound to not sound like its really slow and deep?? 

Thanks!

---

### Post by jtk on 2005-12-31
I don't know how much this is going to help, but do you have alsatools installed?

[http://alsa.opensrc.org/index.php?page=Envy24Control](http://alsa.opensrc.org/index.php?page=Envy24Control)

---

### Post by Imrik on 2006-01-01
I had the same problem when I first installed Breezy and UT2004. You start the game  and instead of no sound at all (which is usually the problem) you get sluggish almost slo-mo sound. I think it has something to do with using Envy24 audio (which I do).

Anyway, what I did to fix it was copy the libSDL-1.2.so.0 and openal.so from the system folder of an America's Army installation to the system folder of my UT2004 installation. I've also done this using the demo version of UT2004 instead of ArmyOps, and it seems to work flawlessly afterwards.

Some of my friends say that after doing this they end up with no sound at all, but I found that killing esd and then running the game solves that little problem, y'know, should it happen to anyone who reads this.

Hope that helps, good luck.

---

### Post by jimchristopher on 2006-01-03
well, I tried 4 different versions of alsa tools and none would complie right for me.  GTK errors? 

I think I'll try the ut2004 demo file copy thing....

---

### Post by Perfect Storm on 2006-01-03
> well, I tried 4 different versions of alsa tools and none would complie right for me. GTK errors? 

Terminal output is needed if you want help with that.

---

### Post by jimchristopher on 2006-01-03
I installed the demo and after copying this file the sound is working....  UT2004 boots up quite slow now, but the sound works great!!  

thanks lmrik!!!!!!!!!!!!!!!!!1

---

### Post by Imrik on 2006-01-03
[QUOTE=jimchristopher]I installed the demo and after copying this file the sound is working....  UT2004 boots up quite slow now, but the sound works great!!  

thanks lmrik!!!!!!!!!!!!!!!!!1[/QUOTE]

No problem. I signed up here just to help you out since it irritated me to no end.
Have fun with UT. :p

---

### Post by jimchristopher on 2006-01-03
HMPF

the struggle continues....  this morning when I tried installing the demo and copying the sound files it worked great.  I'm almost thinking now that I just accidentally started up the demo? and it was working?  then I posted and went to work.  When I get home tonight to try it out, sound is still sluggish and now the demo wont even execute at all.  I tried copying the files again, but no luck.

---

### Post by jimchristopher on 2006-01-03
I downloaded alsatools1.0.9 and ./configure fine, but this is what I get when I make envy24tools:  some edits to fit size restrictions

envy24control.c:675: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:675: error: parse error before "rate_locking_toggled"
envy24control.c:684: error: parse error before "rate_reset_toggled"
envy24control.c: At top level:
envy24control.c:689: error: parse error before '*' token
envy24control.c: In function `create_actual_rate':
envy24control.c:691: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:691: error: `frame' undeclared (first use in this function)
envy24control.c:692: error: `label' undeclared (first use in this function)
envy24control.c:696: error: `box' undeclared (first use in this function)
envy24control.c:696: error: `TRUE' undeclared (first use in this function)
envy24control.c:702: error: `GTK_JUSTIFY_LEFT' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:706: error: parse error before '*' token
envy24control.c: In function `create_volume_change':
envy24control.c:708: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:708: error: `frame' undeclared (first use in this function)
envy24control.c:709: error: `hbox' undeclared (first use in this function)
envy24control.c:710: error: `GtkObject' undeclared (first use in this function)
envy24control.c:710: error: `spinbutton_adj' undeclared (first use in this function)
envy24control.c:711: error: `spinbutton' undeclared (first use in this function)envy24control.c:712: error: `label' undeclared (first use in this function)
envy24control.c:716: error: `box' undeclared (first use in this function)
envy24control.c:716: error: `TRUE' undeclared (first use in this function)
envy24control.c:718: error: `FALSE' undeclared (first use in this function)
envy24control.c:726: error: `GTK_JUSTIFY_LEFT' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:739: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_profi_data':
envy24control.c:741: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:741: error: `frame' undeclared (first use in this function)
envy24control.c:742: error: `vbox' undeclared (first use in this function)
envy24control.c:743: error: `radiobutton' undeclared (first use in this function)
envy24control.c:744: error: `GSList' undeclared (first use in this function)
envy24control.c:744: error: `group' undeclared (first use in this function)
envy24control.c:748: error: `box' undeclared (first use in this function)
envy24control.c:748: error: `FALSE' undeclared (first use in this function)
envy24control.c:748: error: `TRUE' undeclared (first use in this function)
envy24control.c:763: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:763: error: parse error before "profi_data_toggled"
envy24control.c:772: error: parse error before "profi_data_toggled"
envy24control.c: At top level:
envy24control.c:776: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_profi_stream':
envy24control.c:778: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:778: error: `frame' undeclared (first use in this function)
envy24control.c:779: error: `vbox' undeclared (first use in this function)
envy24control.c:780: error: `radiobutton' undeclared (first use in this function)
envy24control.c:781: error: `GSList' undeclared (first use in this function)
envy24control.c:781: error: `group' undeclared (first use in this function)
envy24control.c:785: error: `box' undeclared (first use in this function)
envy24control.c:785: error: `FALSE' undeclared (first use in this function)
envy24control.c:785: error: `TRUE' undeclared (first use in this function)
envy24control.c:799: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:799: error: parse error before "profi_stream_toggled"
envy24control.c:808: error: parse error before "profi_stream_toggled"
envy24control.c: At top level:
envy24control.c:812: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_profi_emphasis':
envy24control.c:814: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:814: error: `frame' undeclared (first use in this function)
envy24control.c:815: error: `vbox' undeclared (first use in this function)
envy24control.c:816: error: `radiobutton' undeclared (first use in this function)
envy24control.c:817: error: `GSList' undeclared (first use in this function)
envy24control.c:817: error: `group' undeclared (first use in this function)
envy24control.c:821: error: `box' undeclared (first use in this function)
envy24control.c:821: error: `FALSE' undeclared (first use in this function)
envy24control.c:821: error: `TRUE' undeclared (first use in this function)
envy24control.c:836: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:836: error: parse error before "profi_emphasis_toggled"
envy24control.c:845: error: parse error before "profi_emphasis_toggled"
envy24control.c:854: error: parse error before "profi_emphasis_toggled"
envy24control.c:863: error: parse error before "profi_emphasis_toggled"
envy24control.c: At top level:
envy24control.c:867: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_profi':
envy24control.c:869: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:869: error: `hbox' undeclared (first use in this function)
envy24control.c:870: error: `vbox' undeclared (first use in this function)
envy24control.c:871: error: `label' undeclared (first use in this function)
envy24control.c:873: error: `FALSE' undeclared (first use in this function)
envy24control.c:875: error: `notebook' undeclared (first use in this function)
envy24control.c:880: error: `page' undeclared (first use in this function)
envy24control.c:885: error: `TRUE' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:899: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_consumer_copyright':
envy24control.c:901: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:901: error: `frame' undeclared (first use in this function)
envy24control.c:902: error: `vbox' undeclared (first use in this function)
envy24control.c:903: error: `radiobutton' undeclared (first use in this function)
envy24control.c:904: error: `GSList' undeclared (first use in this function)
envy24control.c:904: error: `group' undeclared (first use in this function)
envy24control.c:908: error: `box' undeclared (first use in this function)
envy24control.c:908: error: `FALSE' undeclared (first use in this function)
envy24control.c:908: error: `TRUE' undeclared (first use in this function)
envy24control.c:922: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:922: error: parse error before "consumer_copyright_toggled"
envy24control.c:931: error: parse error before "consumer_copyright_toggled"
envy24control.c: At top level:
envy24control.c:935: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_consumer_copy':
envy24control.c:937: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:937: error: `frame' undeclared (first use in this function)
envy24control.c:938: error: `vbox' undeclared (first use in this function)
envy24control.c:939: error: `radiobutton' undeclared (first use in this function)
envy24control.c:940: error: `GSList' undeclared (first use in this function)
envy24control.c:940: error: `group' undeclared (first use in this function)
envy24control.c:944: error: `box' undeclared (first use in this function)
envy24control.c:944: error: `FALSE' undeclared (first use in this function)
envy24control.c:944: error: `TRUE' undeclared (first use in this function)
envy24control.c:958: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:958: error: parse error before "consumer_copy_toggled"
envy24control.c:967: error: parse error before "consumer_copy_toggled"
envy24control.c: At top level:
envy24control.c:971: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_consumer_emphasis':
envy24control.c:973: error: `GtkWidget' undeclared (first use in this function)
envy24control.c:973: error: `frame' undeclared (first use in this function)
envy24control.c:974: error: `vbox' undeclared (first use in this function)
envy24control.c:975: error: `radiobutton' undeclared (first use in this function)
envy24control.c:976: error: `GSList' undeclared (first use in this function)
envy24control.c:976: error: `group' undeclared (first use in this function)
envy24control.c:980: error: `box' undeclared (first use in this function)
envy24control.c:980: error: `FALSE' undeclared (first use in this function)
envy24control.c:980: error: `TRUE' undeclared (first use in this function)
envy24control.c:993: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:993: error: parse error before "consumer_emphasis_toggled"
envy24control.c:1002: error: parse error before "consumer_emphasis_toggled"
envy24control.c: At top level:
envy24control.c:1006: error: parse error before '*' token
envy24control.c: In function `create_spdif_output_settings_consumer_category':
envy24control.c:1008: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1008: error: `frame' undeclared (first use in this function)
envy24control.c:1009: error: `vbox' undeclared (first use in this function)
envy24control.c:1010: error: `radiobutton' undeclared (first use in this function)
envy24control.c:1011: error: `GSList' undeclared (first use in this function)
envy24control.c:1011: error: `group' undeclared (first use in this function)
envy24control.c:1015: error: `box' undeclared (first use in this function)
envy24control.c:1015: error: `FALSE' undeclared (first use in this function)
envy24control.c:1015: error: `TRUE' undeclared (first use in this function)
envy24control.c:1028: error: `GtkSignalFunc' undeclared (first use in this function)

envy24control.c:1200: error: `vbox' undeclared (first use in this function)
envy24control.c:1201: error: `radiobutton' undeclared (first use in this function)
envy24control.c:1202: error: `GSList' undeclared (first use in this function)
envy24control.c:1202: error: `group' undeclared (first use in this function)
envy24control.c:1210: error: `box' undeclared (first use in this function)
envy24control.c:1210: error: `FALSE' undeclared (first use in this function)
envy24control.c:1210: error: `TRUE' undeclared (first use in this function)
envy24control.c:1224: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:1224: error: parse error before "spdif_on_off_toggled"
envy24control.c:1233: error: parse error before "spdif_on_off_toggled"
envy24control.c: At top level:
envy24control.c:1240: error: parse error before '*' token
envy24control.c: In function `create_breakbox_led':
envy24control.c:1242: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1242: error: `frame' undeclared (first use in this function)
envy24control.c:1243: error: `vbox' undeclared (first use in this function)
envy24control.c:1244: error: `radiobutton' undeclared (first use in this function)
envy24control.c:1245: error: `GSList' undeclared (first use in this function)
envy24control.c:1245: error: `group' undeclared (first use in this function)
envy24control.c:1253: error: `box' undeclared (first use in this function)
envy24control.c:1253: error: `FALSE' undeclared (first use in this function)
envy24control.c:1253: error: `TRUE' undeclared (first use in this function)
envy24control.c:1267: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:1267: error: parse error before "breakbox_led_toggled"
envy24control.c:1276: error: parse error before "breakbox_led_toggled"
envy24control.c: At top level:
envy24control.c:1283: error: parse error before '*' token
envy24control.c: In function `create_phono_input':
envy24control.c:1285: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1285: error: `frame' undeclared (first use in this function)
envy24control.c:1286: error: `vbox' undeclared (first use in this function)
envy24control.c:1287: error: `radiobutton' undeclared (first use in this function)
envy24control.c:1288: error: `GSList' undeclared (first use in this function)
envy24control.c:1288: error: `group' undeclared (first use in this function)
envy24control.c:1296: error: `box' undeclared (first use in this function)
envy24control.c:1296: error: `FALSE' undeclared (first use in this function)
envy24control.c:1296: error: `TRUE' undeclared (first use in this function)
envy24control.c:1310: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:1310: error: parse error before "phono_input_toggled"
envy24control.c:1319: error: parse error before "phono_input_toggled"
envy24control.c: At top level:
envy24control.c:1326: error: parse error before '*' token
envy24control.c: In function `create_input_interface':
envy24control.c:1328: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1328: error: `frame' undeclared (first use in this function)
envy24control.c:1329: error: `vbox' undeclared (first use in this function)
envy24control.c:1330: error: `radiobutton' undeclared (first use in this function)
envy24control.c:1331: error: `GSList' undeclared (first use in this function)
envy24control.c:1331: error: `group' undeclared (first use in this function)
envy24control.c:1339: error: `box' undeclared (first use in this function)
envy24control.c:1339: error: `FALSE' undeclared (first use in this function)
envy24control.c:1339: error: `TRUE' undeclared (first use in this function)
envy24control.c:1353: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:1353: error: parse error before "analog_input_select_toggled"
envy24control.c:1362: error: parse error before "analog_input_select_toggled"
envy24control.c:1371: error: parse error before "analog_input_select_toggled"
envy24control.c:1380: error: parse error before "analog_input_select_toggled"
envy24control.c: At top level:
envy24control.c:1387: error: parse error before '*' token
envy24control.c: In function `create_hardware':
envy24control.c:1389: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1389: error: `label' undeclared (first use in this function)
envy24control.c:1390: error: `hbox' undeclared (first use in this function)
envy24control.c:1391: error: `vbox' undeclared (first use in this function)
envy24control.c:1392: error: `vbox2' undeclared (first use in this function)
envy24control.c:1394: error: `FALSE' undeclared (first use in this function)
envy24control.c:1396: error: `notebook' undeclared (first use in this function)
envy24control.c:1400: error: `page' undeclared (first use in this function)
envy24control.c:1406: error: `TRUE' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:1428: error: parse error before '*' token
envy24control.c: In function `create_about':
envy24control.c:1430: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1430: error: `label' undeclared (first use in this function)
envy24control.c:1431: error: `vbox' undeclared (first use in this function)
envy24control.c:1433: error: `FALSE' undeclared (first use in this function)
envy24control.c:1435: error: `notebook' undeclared (first use in this function)
envy24control.c:1441: error: `page' undeclared (first use in this function)
envy24control.c:1446: error: `TRUE' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:1469: error: parse error before '*' token
envy24control.c: In function `create_analog_volume':
envy24control.c:1471: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1471: error: `label' undeclared (first use in this function)
envy24control.c:1472: error: `hbox' undeclared (first use in this function)
envy24control.c:1473: error: `vbox' undeclared (first use in this function)
envy24control.c:1474: error: `frame' undeclared (first use in this function)
envy24control.c:1475: error: `GtkObject' undeclared (first use in this function)envy24control.c:1475: error: `adj' undeclared (first use in this function)
envy24control.c:1476: error: `vscale' undeclared (first use in this function)
envy24control.c:1477: error: `radiobutton' undeclared (first use in this function)
envy24control.c:1478: error: `GSList' undeclared (first use in this function)
envy24control.c:1478: error: `group' undeclared (first use in this function)
envy24control.c:1479: error: `scrolledwindow' undeclared (first use in this function)
envy24control.c:1480: error: `viewport' undeclared (first use in this function)
envy24control.c:1502: error: `notebook' undeclared (first use in this function)
envy24control.c:1507: error: `page' undeclared (first use in this function)
envy24control.c:1511: error: `GTK_POLICY_ALWAYS' undeclared (first use in this function)
envy24control.c:1511: error: `GTK_POLICY_NEVER' undeclared (first use in this function)
envy24control.c:1516: error: `FALSE' undeclared (first use in this function)
envy24control.c:1527: error: `TRUE' undeclared (first use in this function)
envy24control.c:1551: error: `gpointer' undeclared (first use in this function)
envy24control.c:1551: error: parse error before "long"
envy24control.c:1554: error: `GtkLabel' undeclared (first use in this function)
envy24control.c:1554: error: parse error before ')' token
envy24control.c:1568: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:1568: error: parse error before "dac_sense_toggled"
envy24control.c:1604: error: `GTK_POS_BOTTOM' undeclared (first use in this function)
envy24control.c:1608: error: parse error before "long"
envy24control.c:1611: error: parse error before ')' token
envy24control.c:1624: error: parse error before "adc_sense_toggled"
envy24control.c:1664: error: parse error before "long"
envy24control.c:1667: error: parse error before ')' token
envy24control.c: In function `index_active_profile':
envy24control.c:1675: error: `gint' undeclared (first use in this function)
envy24control.c:1675: error: parse error before "index"
envy24control.c:1676: error: `gboolean' undeclared (first use in this function)
envy24control.c:1678: error: `found' undeclared (first use in this function)
envy24control.c:1678: error: `FALSE' undeclared (first use in this function)
envy24control.c:1679: error: invalid lvalue in assignment
envy24control.c:1679: warning: comparison between pointer and integer
envy24control.c:1679: error: wrong type argument to increment
envy24control.c:1681: error: array subscript is not an integer
envy24control.c:1682: error: `TRUE' undeclared (first use in this function)
envy24control.c:1688: warning: return makes integer from pointer without a cast
envy24control.c: At top level:
envy24control.c:1693: error: parse error before '*' token
envy24control.c: In function `delete_card_number':
envy24control.c:1695: error: `gint' undeclared (first use in this function)
envy24control.c:1695: error: parse error before "res"
envy24control.c:1699: error: `delete_button' undeclared (first use in this function)
envy24control.c:1699: error: invalid type argument of `->'
envy24control.c:1702: error: `card_nr' undeclared (first use in this function)
envy24control.c:1702: error: invalid type argument of `->'
envy24control.c:1705: error: `FALSE' undeclared (first use in this function)
envy24control.c:1709: error: `res' undeclared (first use in this function)
envy24control.c:1715: error: invalid lvalue in assignment
envy24control.c:1715: warning: comparison between pointer and integer
envy24control.c:1715: error: wrong type argument to increment
envy24control.c:1717: error: array subscript is not an integer
envy24control.c:1717: warning: passing arg 1 of `get_profile_name' makes integer from pointer without a cast
envy24control.c: At top level:
envy24control.c:1726: error: parse error before "profile_number"
envy24control.c: In function `restore_active_profile':
envy24control.c:1728: error: `gint' undeclared (first use in this function)
envy24control.c:1728: error: parse error before "res"
envy24control.c:1730: error: `res' undeclared (first use in this function)
envy24control.c:1730: error: `profile_number' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:1735: error: parse error before '*' token
envy24control.c: In function `save_active_profile':
envy24control.c:1737: error: `gint' undeclared (first use in this function)
envy24control.c:1737: error: parse error before "res"
envy24control.c:1740: error: `save_button' undeclared (first use in this function)
envy24control.c:1740: error: invalid type argument of `->'
envy24control.c:1742: error: invalid lvalue in assignment
envy24control.c:1743: error: `res' undeclared (first use in this function)
envy24control.c:1743: error: array subscript is not an integer
envy24control.c:1743: warning: passing arg 2 of `save_restore' makes integer from pointer without a cast
envy24control.c:1743: warning: passing arg 5 of `save_restore' makes pointer from integer without a cast
envy24control.c:1747: error: `FALSE' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:1756: error: parse error before '*' token
envy24control.c: In function `entry_toggle_editable':
envy24control.c:1758: error: `gint' undeclared (first use in this function)
envy24control.c:1758: error: parse error before "index"
envy24control.c:1761: error: `toggle_button' undeclared (first use in this function)
envy24control.c:1762: error: `TRUE' undeclared (first use in this function)
envy24control.c:1766: error: invalid type argument of `->'
envy24control.c:1769: error: invalid type argument of `->'
envy24control.c:1770: error: invalid type argument of `->'
envy24control.c:1772: error: `profile_number' undeclared (first use in this function)
envy24control.c:1773: error: invalid lvalue in assignment
envy24control.c:1773: warning: comparison between pointer and integer
envy24control.c:1773: error: wrong type argument to increment
envy24control.c:1775: error: array subscript is not an integer
envy24control.c:1776: error: array subscript is not an integer
envy24control.c:1776: error: `FALSE' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:1786: error: parse error before '*' token
envy24control.c: In function `enter_callback':
envy24control.c:1788: error: syntax error before '*' token
envy24control.c:1789: error: `entry_text' undeclared (first use in this function)
envy24control.c: At top level:
envy24control.c:1793: error: parse error before '*' token
envy24control.c:1793: error: parse error before '*' token
envy24control.c: In function `toggle_button_entry':
envy24control.c:1795: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1795: error: `box' undeclared (first use in this function)
envy24control.c:1796: error: `entry_label' undeclared (first use in this function)
envy24control.c:1797: error: `toggle_button' undeclared (first use in this function)
envy24control.c:1799: error: `FALSE' undeclared (first use in this function)
envy24control.c:1804: error: array subscript is not an integer
envy24control.c:1806: error: `profile_name' undeclared (first use in this function)
envy24control.c:1811: error: `gpointer' undeclared (first use in this function)
envy24control.c:1811: error: parse error before "entry_label"
envy24control.c:1814: error: parse error before "entry_label"
envy24control.c: At top level:
envy24control.c:1824: error: parse error before '*' token
envy24control.c: In function `create_profiles':
envy24control.c:1826: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1826: error: `label' undeclared (first use in this function)
envy24control.c:1827: error: `label_card_nr' undeclared (first use in this function)
envy24control.c:1828: error: `vbox' undeclared (first use in this function)
envy24control.c:1829: error: `vbox1' undeclared (first use in this function)
envy24control.c:1830: error: `hbox1' undeclared (first use in this function)
envy24control.c:1831: error: `hbox2' undeclared (first use in this function)
envy24control.c:1832: error: `save_button' undeclared (first use in this function)
envy24control.c:1833: error: `delete_button' undeclared (first use in this function)
envy24control.c:1834: error: `GtkObject' undeclared (first use in this function)envy24control.c:1834: error: `card_button_adj' undeclared (first use in this function)
envy24control.c:1835: error: `card_button' undeclared (first use in this function)
envy24control.c:1836: error: `gint' undeclared (first use in this function)
envy24control.c:1836: error: parse error before "index"
envy24control.c:1838: error: `gchar' undeclared (first use in this function)
envy24control.c:1838: error: `profile_name' undeclared (first use in this function)
envy24control.c:1839: error: parse error before "max_profiles"
envy24control.c:1842: error: `FALSE' undeclared (first use in this function)
envy24control.c:1844: error: `notebook' undeclared (first use in this function)
envy24control.c:1850: error: `page' undeclared (first use in this function)
envy24control.c:1855: error: invalid lvalue in assignment
envy24control.c:1855: warning: comparison between pointer and integer
envy24control.c:1855: error: wrong type argument to increment
envy24control.c:1857: warning: passing arg 1 of `get_profile_name' makes integer from pointer without a cast
envy24control.c:1858: error: array subscript is not an integer
envy24control.c:1859: error: array subscript is not an integer
envy24control.c:1876: error: `GTK_JUSTIFY_LEFT' undeclared (first use in this function)
envy24control.c:1882: error: `TRUE' undeclared (first use in this function)
envy24control.c:1910: error: `max_profiles' undeclared (first use in this function)
envy24control.c:1910: error: `max_digits' undeclared (first use in this function)
envy24control.c:1914: error: `profile_number' undeclared (first use in this function)
envy24control.c: In function `main':
envy24control.c:1947: error: `GtkWidget' undeclared (first use in this function)envy24control.c:1947: error: `notebook' undeclared (first use in this function)
envy24control.c:2134: error: `GTK_WINDOW_TOPLEVEL' undeclared (first use in this function)
envy24control.c:2134: warning: assignment makes pointer from integer without a cast
envy24control.c:2137: error: `GtkSignalFunc' undeclared (first use in this function)
envy24control.c:2137: error: parse error before "gtk_main_quit"
envy24control.c:2138: error: `gtk_main_quit' undeclared (first use in this function)
envy24control.c:2161: error: `GDK_INPUT_READ' undeclared (first use in this function)
make: *** [envy24control.o] Error 1

---

### Post by jimchristopher on 2006-01-08
I think I've got it narrowed down to the simple fact that driver support in alsa is rudimentary for the onboard Envy 24 sound chip on  my SN25P.  Things work well while listening to mp3s while surfing etc, but I cant play games with it.  I pretty much confirmed this by formatting my ubuntu install and trying SUSE 10 and Fedora Core 4.  SUSE was fine except for UT2004, but I had problems right from the start with sound in FC4.  

at this point i've (temporarily) traded my ATI X800XL to a friend for his NV6600GT.  And I was thinking about buying a 7800GT or 6800GS.  But to truly be able to enjoy staying with linux only, I think I'm going to have to buy an external SBLive or something as well.

I'll check to see if there's any progress with this from any ubuntu users with an ENVY24PT/HT that have any tips, till then I'll probably just boot XP...

---

### Post by croissance on 2006-10-13
had similar problem with envy 24 card  & ut2004

libSDL is ok though not optimal
openal.so in ut2004/System is the cause of sound problem


you can download source code 
svn checkout [http://www.openal.org/repos/openal/trunk](http://www.openal.org/repos/openal/trunk) openal

compile and install
sudo cp ./openal.so ./openal.so.original
sudo cp /usr/local/lib/libopenal.so.1.0.0 ./openal.so

while you're at it why not optimise it and get a few extra frames

NOTE if the above makes no sense to you then don't just blindly type stuff in

worked for me

---

### Post by rgd2 on 2006-11-02
> **jtk said:**
> I don't know how much this is going to help, but do you have alsatools installed?

[http://alsa.opensrc.org/index.php?page=Envy24Control](http://alsa.opensrc.org/index.php?page=Envy24Control)

I think this is on the wrong track - i've also got exactly the same problem with ut2004, on a shuttle SN25P as well.
However, i'm running under Gentoo.

Envy24Control is for ice1712 chipsets, it doesn't seem to support my ice1724...
I already had it installed along with alsa-tools.

Prior to an 'emerge --update world' (bringing everything up to date as defined by portage - call it an analog of 'apt-get dist-upgrade' ),
I had the slow audio issue with ut2004 and also with unreal-tournament.

What seemed to work was just to quit and re-run either until the sound playback was correct... however this workaround works no longer.

I strongly suspect the libSDL-1.2.so.0 library sitting in ut2004/System ...
I had replaced openal.so with one built by my system for amd64, and there didn't seem any change.
I overlooked libSDL initially because i just looked for *so in /System... oops.](*,) 

Changing it for the one my system built - specifically 
```

# On a gentoo box! YMMV
mv libSDL-1.2.so.0 backuplibSDL-1.2.so.0
cp /usr/lib64/libSDL-1.2.so.0.11.0  /opt/ut2004/System/libSDL-1.2.so.0
```

Seems to have fixed the slow sound.

Be careful with the above - I'm not sure whether the absolute paths are correct for Ubuntu.


Sidenote: I wonder whether the issue is related to the old libraries included with ut2004 being 32bit and the new ones I've substituted in being 64bit... i am running the 64 bit amd64 ut2004 binary...
When the sound plays slow, it does seems to be playing at half-rate, doesn't it?
Just idle speculation.

Anyway, i hope this was helpful.

---

### Post by jimchristopher on 2006-11-06
So, I've recently started playing with Ubuntu again, and I'd really like to get a gaming fix and not have to boot to windows.  I'm running 6.10 with Beta 9625 Nvidia drivers and Beryl.  My UT2004 is just as borked as ever... sloooow sound.  I tried some of the latest tips offered, but after downloading and maybe? compiling openAL, I dont see a .so file to overwrite my old one with.  Any other tips from anyone about how to get a working .so file or whatever I need??

Thanks!!

---

### Post by Perfect Storm on 2006-11-06
If you really want to game on ubuntu I suggest switch from 64 bit to 32 bit until 64 bit version gets more reliable.

---

### Post by jimchristopher on 2006-11-06
I've never installed a 64 bit version of linux... this is a 32bit Edgy system.  Had the same problem with several versions of Linux (Fedora, Suse, Ubuntu) all 32 bit.  And with the same onboard Envy24 chip.

---

### Post by jimchristopher on 2006-11-07
AAAAAAAAAAAHHH HAHAHAHA!!!!!!

Working now.. went over a bunch of posts about alsamixer and decided to look there again. Run alsamixer and right arrow scroll through all the options.  The one that I needed is one from the last. Multi Track Rate Locking.  Hit M to enable/disable it.  I need it on for my Envy24 chip built into my Shuttle SN25P.  WooHoo!!!  Thanks to everyone that kept pointing me in many directions... one of them worked!!

Off to install the full version and play... watch out for DeathChicken!!!!!!

---

### Post by Perfect Storm on 2006-11-07
congratz ^_^

(by the way, it's a good idea to fill out User CP option on which Ubuntu system you're using, it's easier for people to help with troubleshooting :) )

---


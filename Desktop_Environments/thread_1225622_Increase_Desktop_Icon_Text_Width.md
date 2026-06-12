---
title: "Increase Desktop Icon Text Width"
date: 2009-07-28
forum: Desktop Environments
---

### Post by WillSmith182 on 2009-07-28
I've been looking around for the past few days and can't seem to find an answer to this..

Is there a way to increase the number of characters per line for desktop icons? I can decrease the text size, but that makes thing harder to read! Wider, which is what I wanted but way too small. For example:

Rhythmbox

will appear as 

Rhythmbo
x

I'm under the impression the desktop is "looked after" by nautilus, so am i trying to customise nautilus or gnome?

can anyone help?

---

### Post by orbish on 2009-07-28
I've seen in it gconf-editor.

Try apps>nautilus... might be in there.

---

### Post by mcduck on 2009-07-29
> **WillSmith182 said:**
> I've been looking around for the past few days and can't seem to find an answer to this..

Is there a way to increase the number of characters per line for desktop icons? I can decrease the text size, but that makes thing harder to read! Wider, which is what I wanted but way too small. For example:

Rhythmbox

will appear as 

Rhythmbo
x

I'm under the impression the desktop is "looked after" by nautilus, so am i trying to customise nautilus or gnome?

can anyone help?
The width depends on the icon size. Your only options are to either use smaller text or bigger icons..

---

### Post by WillSmith182 on 2009-07-29
> **orbish said:**
> I've seen in it gconf-editor.

Try apps>nautilus... might be in there.


   [FONT=Trebuchet MS][SIZE=2]Yea I was looking around gconf in the obvious places of desktop and things, obviously found nothing.

I’ve tried searching for any keys relating to width and the "pattern is not found", trying variations like *width* etc but not sure if wildcards work!

I'll have another look tonight and report back.[/SIZE][/FONT]

---

### Post by WillSmith182 on 2009-07-29
> **mcduck said:**
> The width depends on the icon size. Your only options are to either use smaller text or bigger icons..

[FONT=Trebuchet MS]
[/FONT]    [FONT=Trebuchet MS][SIZE=2]See I though that, stretching icons increases the "picture" size but not the length of text allowed. 

Smaller text fits more chars per line, but I want to actually increase the size allowed for text regardless of size (icon or text). Surely there is a 'class'(?) that I can edit or modify to for example increase the size of the object that holds the text value? 

I hope that makes sense, i'm not all that clued up on Linux yet, I started with horrible windows and VB, which makes it even harder![/SIZE][/FONT]

---

### Post by WillSmith182 on 2009-07-30
> **mcduck said:**
> The width depends on the icon size. Your only options are to either use smaller text or bigger icons..

I have tried resizing icons, the text width does not change. there is no relation to the text "label" size.

i have also been looking in gconf-editor,

here is a sample fo search results for "width"

/desktop/gnome/peripherals/keyboard/preview/width
/apps/gnome-volume-control/ui/window_width
/apps/stickynotes_applet/defaults/width
/apps/nautilus-actions/nact_edit_dialog_size_width
/apps/nautilus-actions/nact_im_ex_dialog_size_width
/apps/nautilus-actions/nact_main_dialog_size_width
/apps/deskbar/window_width
/apps/deskbar/entry_width
/apps/rhythmbox/state/window_width
/apps/rhythmbox/state/small_width
/apps/gnometris/saved/width
/apps/gucharmap/width
/apps/gnome-search-tool/default_window_width
/apps/screem/editor/tabwidth
/apps/miro/window/width
/apps/nautilus/compact_view/all_columns_have_same_width
/apps/nautilus/preferences/sidebar_width
/apps/same-gnome/custom_width
/apps/tomboy/search_window_width
/apps/procman/width
/apps/procman/disktreenew/col_2_width
/apps/procman/disktreenew/col_5_width
/apps/procman/disktreenew/col_1_width
/apps/procman/disktreenew/col_4_width
/apps/procman/disktreenew/col_0_width
/apps/procman/disktreenew/col_3_width
/apps/procman/disktreenew/col_6_width
/apps/procman/proctree/col_9_width
/apps/procman/proctree/col_8_width
/apps/procman/proctree/col_7_width
/apps/procman/proctree/col_6_width
/apps/procman/proctree/col_5_width
/apps/procman/proctree/col_4_width
/apps/procman/proctree/col_16_width
/apps/procman/proctree/col_15_width
/apps/procman/proctree/col_3_width
/apps/procman/proctree/col_2_width
/apps/procman/proctree/col_1_width
/apps/procman/proctree/col_0_width
/apps/procman/proctree/col_14_width
/apps/procman/proctree/col_13_width
/apps/procman/proctree/col_12_width
/apps/procman/proctree/col_11_width
/apps/procman/proctree/col_10_width
/apps/file-roller/listing/name_column_width
/apps/file-roller/ui/window_width
/apps/file-roller/ui/sidebar_width
/apps/file-roller/dialogs/last_output/width
/apps/evolution/shell/view_defaults/width
/apps/evolution/shell/view_defaults/folder_bar/width
/apps/evolution/mail/send_recv_width
/apps/evolution/mail/message_window/width
/apps/evolution/mail/composer/window_width
/apps/evolution/mail/composer/width
/apps/evolution/mail/subscribe_window/width
/apps/banshee-1/player_window/width
/apps/banshee-1/player_window/source_view_width
...a lot of banshee-1 crap and some more crap relating to apps that don't mention gnome or nautilus.

does anyone know the key i need to change? surely someone knows!

---

### Post by mazz0 on 2009-08-12
I want to know this too, although I'm more bothered about normal Nautilus icons than desktop icons, but I expect it's the same.

After having tried for ages to find an answer to this I'm worried it may nto be configurable.  Which is very, very rubbish.

---

### Post by mcduck on 2009-08-12
*Stretching* icons will not change the text field length, but setting the icon size through Nautilus preferences does, and so does setting the zoom level.

Disabling compact layout gives a bit more space for text as well.

(and setting smaller desktop font size of course allows more text in the available space)

---

### Post by WillSmith182 on 2010-02-27
> **mcduck said:**
> *Stretching* icons will not change the text field length, but setting the icon size through Nautilus preferences does, and so does setting the zoom level.

Disabling compact layout gives a bit more space for text as well.

(and setting smaller desktop font size of course allows more text in the available space)


That's great, but what if i want the text to be the same size, there must be someway to edit the nautilis source to allow larger numbers of character, or a larger length in pixels..........

I'm so confused, am i right in presuming its nautilus that looks after my icons in folders and on my desktop?

---

### Post by rclowery on 2010-04-01
Did the original poster of this message ever fix his or her problem?

I am having the same issue with my desktop icon size, although the icons in 
the file browser have no such problem.

It would be very hard for me to believe that this isn't a fixable issue.

---

### Post by mcduck on 2010-04-01
> **rclowery said:**
> Did the original poster of this message ever fix his or her problem?

I am having the same issue with my desktop icon size, although the icons in 
the file browser have no such problem.

It would be very hard for me to believe that this isn't a fixable issue.

The only solution (at least apart from downloading the source code for Nautilus, and modifying it yourself) is what I've been telling here: set your icon size larger and you get more text. Apart from that there is no way to control it, the space reserved for text comes directly from the icon size. Larger icons, more room for text.

For example if you have 64 pixels wide icon, that's also the space reserved for the whole icon (including image & text), so you'll also have a 64 pixels wide area for the text to fit into. Change the icon size to 128 pixels and you'll have 128 pixels worth of space for the text as well. Anything else would result in strange looking icon layouts, with more space reserved for the text than for the icon you'd end with more empty space between the icons compared to the size of the icon itself. Nice perhaps if you have very long file names on all the icons, but definitely strange if the icons have normal amounts of text.

---

### Post by Pifilatakanemu on 2010-05-03
Hm, this seems to be a dirty workaround.


It should be possible to say "min. characters per line" for the filenames on the desktop...

---

### Post by WillSmith182 on 2010-05-03
> **flohmann said:**
> Hm, this seems to be a dirty workaround.


It should be possible to say "min. characters per line" for the filenames on the desktop...


this is what i'm trying to achieve, it could jut be clever and utilize some form of auto wrap but also have an upper limit. i think i may have to start my own project on this; although i have no experience of this kind, i'm a VBA/VB.net man so i'm a little out of my depth

---

### Post by Pifilatakanemu on 2010-06-08
*push*

---

### Post by rockoprem on 2010-06-08
Isn't it just right click on Desktop->Change Desktop background->Fonts->Desktop Font->Size... ?? :confused:
Or have I not understood the question??

---

### Post by sonrock3 on 2010-09-09
I had same problem.
Then found
Nautilus settings > unclick "compact" view
allowed icon text width to widen.
Stephen

---


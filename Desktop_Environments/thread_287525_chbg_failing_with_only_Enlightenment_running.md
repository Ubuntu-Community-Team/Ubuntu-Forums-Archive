---
title: "chbg failing with only Enlightenment running"
date: 2006-10-28
forum: Desktop Environments
---

### Post by hampton275 on 2006-10-28
Well I have always used E as my WM and chbg as my swiss army knife wallpaper management/control.
I recently bought an 1.87 Intel core Duo system and am using an Nvidia 6800(used previously) and a freshly installed Xubuntu system(patched to today).
I installed chbg from package and it installed and "starts" fine, but when I try to run with a profile it crashes with:
$ chbg 

Gtk-WARNING **: invalid cast from (NULL) pointer to `GtkLabel'

Gtk-CRITICAL **: file gtklabel.c: line 260 (gtk_label_set_text): assertion `GTK_IS_LABEL (label)' failed.
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 19820 error_code 8 request_code 70 minor_code 0
Gdk-ERROR **: BadMatch (invalid parameter attributes)
  serial 19823 error_code 8 request_code 146 minor_code 3


So I get the source and compile it and get this:

 make
Making all in src
make[1]: Entering directory `/home/ken/downloads/chbg-1.5/src'
gcc  -DHAVE_ENLIGHTENMENT_SUPPORT -DHAVE_XSS_SUPPORT -DHAVE_ESETROOT_SUPPORT -DHAVE_MKSTEMP -DHAVE_RANDOM -g -O2 -Wall -DHAVE_GDKIMLIB1 -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include -DGETTEXT_NLS -DNLS_DIR="\"/usr/local/share/locale\""  -DDEFAULT_SYS_CHBG_RC="\"/usr/local/etc/chbgrc\""  -o chbg  absimg_gdkimlib1.o absimg_gdkpixbuf.o absimg_imlib1.o absimg_imlib2.o absimg.o banner.o config.o chbg.o chwin.o e.o esetroot.o fnmatch.o gaccel.o gimpgradient.o gprop.o gtkbgpixmap.o gtkclrbutton.o gtkmultirow.o gtkmultirowsel.o gtkselbox.o gui_tools.o operations.o recurse.o setup.o settings.o shader.o shaderpv.o thumb.o xsssupport.o  -L/usr/lib -lgdk_imlib -L/usr/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm  -lc  -lz
absimg.o: In function `absimg_rgb_savePNG':
/home/ken/downloads/chbg-1.5/src/absimg.c:92: undefined reference to `png_create_write_struct'
/home/ken/downloads/chbg-1.5/src/absimg.c:97: undefined reference to `png_create_info_struct'
/home/ken/downloads/chbg-1.5/src/absimg.c:106: undefined reference to `png_init_io'
/home/ken/downloads/chbg-1.5/src/absimg.c:107: undefined reference to `png_set_IHDR'
/home/ken/downloads/chbg-1.5/src/absimg.c:113: undefined reference to `png_convert_from_struct_tm'
/home/ken/downloads/chbg-1.5/src/absimg.c:114: undefined reference to `png_set_tIME'
/home/ken/downloads/chbg-1.5/src/absimg.c:116: undefined reference to `png_write_info'
/home/ken/downloads/chbg-1.5/src/absimg.c:124: undefined reference to `png_write_image'
/home/ken/downloads/chbg-1.5/src/absimg.c:127: undefined reference to `png_write_end'
/home/ken/downloads/chbg-1.5/src/absimg.c:128: undefined reference to `png_destroy_write_struct'
/home/ken/downloads/chbg-1.5/src/absimg.c:101: undefined reference to `png_destroy_write_struct'
collect2: ld returned 1 exit status
make[1]: *** [chbg] Error 1
make[1]: Leaving directory `/home/ken/downloads/chbg-1.5/src'
make: *** [all-recursive] Error 1

I have checked all the requirements(synaptic would have added them, but I checked anyway, but maybe I missed something?). I can't figure this out. I have used this app for years without a hitch. If anyone has alternative to chbg I would be willing to entertain alternatives.

TIA

PS libpng is installed as well as the devel packages for it.

---

### Post by hampton275 on 2006-11-13
Does anyone have a suggestion? If not, do you have an alternative choice that is WM indipendant.

---

### Post by hermogene on 2006-12-04
I encounter the same pb with Fluxbox on Edgy Eft... my only alternative is to include a wallpapers menu in fluxbox menu, but of course it won't change the wallpaper automatically.
Did you find any solution?
Thanks

---

### Post by nikoz on 2007-05-15
as suggested [here]("http://blogs.anthologique.net/index.php/blog/117")
and [here]("http://gentoo-wiki.com/Xorg_X11_and_Transparency")

add XLIB_SKIP_ARGB_VISUALS=1 before chbg command line
XLIB_SKIP_ARGB_VISUALS=1  chbg -mode ....

tested on Xubuntu 7.04

---


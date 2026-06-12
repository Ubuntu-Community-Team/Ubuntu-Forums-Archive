---
title: "Cannot install GDM login manager"
date: 2007-12-07
forum: Desktop Environments
---

### Post by Jockeo on 2007-12-07
Hi,

I'm trying to install this GDM login manager on my 7.10 Gutsy Gibbon installation: [http://art.gnome.org/themes/gdm_greeter/1277](http://art.gnome.org/themes/gdm_greeter/1277)

I start gdmsetup and drag the Login Manager tarball (the compressed folder) into the theme window and click the install button in the dialog. However, the theme doesn't show up in the theme window. I get the following output to the terminal during installation:
gdmsetup[6259]: Gtk-WARNING: Ignoring the separator setting
gdmsetup[6259]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[6259]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[6259]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[6259]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[6259]: GLib-CRITICAL: g_key_file_get_locale_string: assertion `key_file != NULL' failed
gdmsetup[6259]: GLib-CRITICAL: g_key_file_free: assertion `key_file != NULL' failed

What can be wrong?

NB: If I try to install it again, it sais "Theme directory 'soft-flower-gdm' seems to be already installed. Install again anyway?", so it seems like it is partly installed.

---

### Post by xubis on 2008-02-06
I have this problem as well, but for the widescreen version the same login manager

---

### Post by xubis on 2008-02-06
Ah, install this over the top of it and all works fine, errors go :)
[http://aldeby.wordpress.com/2007/10/12/soft-flower-gnome-login-manager-theme-220x/](http://aldeby.wordpress.com/2007/10/12/soft-flower-gnome-login-manager-theme-220x/)

---

### Post by Jockeo on 2008-02-08
> **xubis said:**
> Ah, install this over the top of it and all works fine, errors go :)
[http://aldeby.wordpress.com/2007/10/12/soft-flower-gnome-login-manager-theme-220x/](http://aldeby.wordpress.com/2007/10/12/soft-flower-gnome-login-manager-theme-220x/)

Thanks xubis, that worked for me as well :)

---

### Post by jfollmann on 2008-03-01
Fixed the problem for me, too. Thanks!

---


---
title: "firefox crash all the time since the past week"
date: 2009-05-19
forum: General Help
---

### Post by sdowney717 on 2009-05-19
I just dont know. It is getting so bad I fired up opera 10 and so far no crashing.
Firefox will just stop responding. And I have to kill it. I have today killed it about 15 times over the last 5 hours.

---

### Post by Kimm on 2009-05-19
Do you happen to be using Flash when it crashes? and are you using 64 or 32 bit?

---

### Post by ispy on 2009-05-19
try running Firefox from the terminal and posting any error messages here.

If we don't know what's wrong, we can't fix it.

---

### Post by sdowney717 on 2009-05-21
ok it just crashed this AM 
I started firefox from terminal yesterday and left it running with 4 tabs open. Worked fine all day.

Today used it for an hour and it has crashed.

this is it
scott@scott-desktop:~$ firefox

shows no errors.

firefox has sinply stopped responding again.
no flash being used. Meaning I am not visiting flash sites. I was posting on Jeep Forum and it just died.

So I had opera open from yesterday, and it is still working.

IF I click on a panel tab for firefox, it will cause the computer screen to stop refreshing including the opera browser and I have to open epiphany. Then opera works again but not firefox.

---

### Post by fduppa on 2009-05-21
you can try to disable all addons and the flash plugin. It may be one of those that is causing the problem. do not uninstall them.. just disable them.


PS: also remember that it has to crash when running from console to see if it has an error output.

---

### Post by sdowney717 on 2009-05-21
crash may not be the best word, stops responding, locks up is what it does. 
And it might be flash plugin. today opera "crashed" when going to youtube, it refused to play video and finally opera stopped responding. Then I fired up Epiphany browser and strangely it freed up opera but firefox was still stuck. 
When this happens I have to reboot. I just installed a kernel update just a few minutes ago so maybe it will improve.

---

### Post by sdowney717 on 2009-06-19
I noticed it started crashing again, so i ran firefox from terminal and this is what I get
It was up for a full day without a crash . I went to a cnn link on john and Kate and it died while reading the page.
[http://www.cnn.com/2009/SHOWBIZ/TV/06/18/jon.kate.announcement/index.html?iref=mpstoryview](http://www.cnn.com/2009/SHOWBIZ/TV/06/18/jon.kate.announcement/index.html?iref=mpstoryview)

[CODE]scott@scott-desktop:~$ firefox

(transmission:11526): Gtk-CRITICAL **: gtk_window_set_urgency_hint: assertion `GTK_IS_WINDOW (window)' failed

(transmission:11526): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(transmission:11526): Gtk-CRITICAL **: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(transmission:11526): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(transmission:11526): Gtk-CRITICAL **: gtk_tree_selection_selected_foreach: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(transmission:11554): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(transmission:11554): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(transmission:11554): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated

(transmission:11554): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated
Segmentation fault
scott@scott-desktop:~$ 
/CODE]

---

### Post by sdowney717 on 2009-06-22
scott@scott-desktop:~$ firefox
Segmentation fault
scott@scott-desktop:~$ 


today it is just seg faulting. This is about 6 times in the last hour.

I went ahead and upgraded to Jaunty. I was avoiding doing this because of the ATI driver mess. no more 3d
But so far no crashes. 
I think I need an nvidia card.

---


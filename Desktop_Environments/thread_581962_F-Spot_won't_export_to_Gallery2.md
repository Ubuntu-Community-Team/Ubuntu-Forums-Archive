---
title: "F-Spot won't export to Gallery2"
date: 2007-10-19
forum: Desktop Environments
---

### Post by wactuary on 2007-10-19
Recently migrated to Gutsy.  Actually I have been  running the Beta versions without issue.  In Feisty, I had F-Spot configured to upload to my Gallery2 install.  After upgrading to Gutsy, I believe it continued to work but I'm not 100% certain.  Recently I purged by F-Spot install and started from scratch (lazy way of getting rid of lots of duplicates in my database).  In trying to re-setup the Export to Web Gallery, I can't get it to work.

Gallery 2.2.4, F-Spot 0.4.0.  Fully up-to-date Ubuntu Desktop 7.10 release.  Apache2, MySQL, PHP5, etc. are all Ubuntu Gutsy installations.

So I Insert the website by using F-Spot - Edit - Export - Export to Web Gallery

I clicked Add and put in my site URL and username/password.  I've tried several including Admin.

Click OK and it brings me back to the upload screen.

Export to album dialog box is grey and has (No Albums).  When I try to click Add, it brings the dialog.  The Parent Directory is empty.  The other three boxes are open, and I can put what I want.  When I click OK, F-Spot hangs indefinitely and needs a Force Quit.

I'm not sure what else to do to debug.

Thanks,
Chris

---

### Post by emway on 2008-05-03
Same over here, and only with Ubuntu. Tried it with Mandriva 2008.1 and no problems (PROBLEMS also in Mandriva 2008.1 Powerpack!, tried Suse11 rc1 and no problems...) with F-spot and gallery.

Gallery created: GalleryRemote.Gallery2
Gallery2: Attempting to login
StatusText : Login successful.
StatusText : No viewable albums.
Error: Unable to parse server response
Exception in Gtk# callback delegate
  Note: Applications can use GLib.ExceptionManager.UnhandledException to handle the exception.
GalleryRemote.GalleryCommandException: Error: Unable to parse server response
  at GalleryRemote.Gallery.ParseBasic (System.Net.HttpWebResponse response) [0x00000] 
  at GalleryRemote.Gallery.ParseNewAlbum (System.Net.HttpWebResponse response) [0x00000] 
  at GalleryRemote.Gallery2.NewAlbum (System.String parent_name, System.String name, System.String title, System.String description) [0x00000] 
  at G2Export.GalleryAddAlbum.HandleAddResponse (System.Object sender, Gtk.ResponseArgs args) [0x00000] 
  at Gtk.Dialog.ResponseSignalCallback (IntPtr arg0, Int32 arg1, IntPtr gch) [0x00000] 
   at GLib.ExceptionManager.RaiseUnhandledException(System.Exception e, Boolean is_terminal)
   at Gtk.Dialog.ResponseSignalCallback(IntPtr arg0, Int32 arg1, IntPtr gch)
   at Gtk.Dialog.ResponseSignalCallback(IntPtr , Int32 , IntPtr )
   at Gtk.Application.gtk_main()
   at Gtk.Application.gtk_main()
   at Gtk.Application.Run()
   at Gnome.Program.Run()
   at FSpot.Driver.Main(System.String[] args)

---


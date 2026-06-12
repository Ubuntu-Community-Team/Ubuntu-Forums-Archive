---
title: "Problem downloading photos from Camera in Jaunty"
date: 2009-05-07
forum: General Help
---

### Post by yundo on 2009-05-07
Good afternoon good people,
 

 I am having trouble downloading pictures to Ubuntu 9.04.from one of my memory cards that I use with  my Nikon D90. I've had a look in these forums with no luck.

 

This memory card worked fine previously and my other memory card has not had any problems.  
 

 With the problematic memory card it downloads about half the photos and then stops.  
 

 The first error displayed is:  
 > Error getting file: -1: Unspecified error
 When I try to view one of the problematic pictures straight from the memory card I get:
 > Failed to open input stream for file
 The full error message I get is:
> An unhandled exception was thrown: Object reference not set to an instance of an object 
  
   at FileImportBackend.Prepare () [0x00000]  
   at ImportCommand.DoImport (.ImportBackend imp) [0x00000]  
   at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags, Boolean copy) [0x00000]  
   at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags) [0x00000]  
   at FSpot.CameraFileSelectionDialog.ImportFiles () [0x00000]  
   at FSpot.CameraFileSelectionDialog.Run () [0x00000]  
   at MainWindow.ImportCamera (System.String camera_device) [0x00000]  
   at FSpot.Core+ImportCommand.Execute () [0x00000]  
   at FSpot.Core.Import (System.String path) [0x00000]  
   at FSpot.Driver.Main (System.String[] args) [0x00000]  
 .NET Version: 2.0.50727.42 
  
 Assembly Version Information: 
  
 libgphoto2-sharp (1.0.3385.23088) 
 SmugMugExport (0.0.0.0) 
 CDExport (0.0.0.0) 
 FlickrExport (0.0.0.0) 
 GalleryExport (0.0.0.0) 
 FolderExport (0.0.0.0) 
 HashJob (0.0.0.0) 
 PicasaWebExport (0.0.0.0) 
 pango-sharp (2.12.0.0) 
 SemWeb (0.7.1.0) 
 glade-sharp (2.12.0.0) 
 FSpot.JobScheduler (0.0.0.0) 
 System.Transactions (2.0.0.0) 
 System.Configuration (2.0.0.0) 
 FSpot.Widgets (0.0.0.0) 
 System.Xml (2.0.0.0) 
 NDesk.DBus.Proxies (0.0.0.0) 
 gconf-sharp (2.24.0.0) 
 System.Data (2.0.0.0) 
 Mono.Data.SqliteClient (2.0.0.0) 
 FSpot.Query (0.0.0.0) 
 gdk-sharp (2.12.0.0) 
 gnome-vfs-sharp (2.24.0.0) 
 NDesk.DBus.GLib (1.0.0.0) 
 NDesk.DBus (1.0.0.0) 
 Cms (0.0.0.0) 
 Mono.Posix (2.0.0.0) 
 System (2.0.0.0) 
 FSpot.Utils (0.0.0.0) 
 FSpot.Core (0.0.0.0) 
 atk-sharp (2.12.0.0) 
 gtk-sharp (2.12.0.0) 
 Mono.Addins (0.4.0.0) 
 Mono.Addins.Setup (0.4.0.0) 
 glib-sharp (2.12.0.0) 
 gnome-sharp (2.24.0.0) 
 f-spot (0.5.0.3) 
 mscorlib (2.0.0.0) 
  
 Platform Information: Linux 2.6.28-11-generic i686 unknown GNU/Linux 
  
 Distribution Information: 
  
 [/etc/debian_version] 
 5.0 
  
 [/etc/lsb-release] 
 DISTRIB_ID=Ubuntu 
 DISTRIB_RELEASE=9.04 
 DISTRIB_CODENAME=jaunty 
 DISTRIB_DESCRIPTION="Ubuntu 9.04" 
 Please share any ideas on how to resolve this with me.  
 

 Thanks

---

### Post by kroiz on 2009-06-16
Same problem here, Different camera though.
Also I AM able to access the camera when it is connected to a different computer w/ ubuntu.

---

### Post by kroiz on 2009-06-16
Also, more than two years ago I had I [posted]("http://ubuntuforums.org/showthread.php?t=361149") a question asking help cause the same camera was not being detected.

I was instructed to edit the file:
/etc/udev/rules.d/40-permissions.rules

now this file does not exist any more.

I was also instructed to change something in:
*System->Prefereces->Removable Drives*

but that too does not exist any more.

Maybe something changed with the last upgrade that messed my settings, cause I think that is about the time it stoped working.

---

### Post by libbresse on 2009-06-21
I also have a Nikon D90 and recieve the same error:

at FileImportBackend.Prepare () [0x00000] 
  at ImportCommand.DoImport (.ImportBackend imp) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags, Boolean copy) [0x00000] 
  at ImportCommand.ImportFromPaths (.PhotoStore store, System.String[] paths, FSpot.Tag[] tags) [0x00000] 
  at FSpot.CameraFileSelectionDialog.ImportFiles () [0x00000] 
  at FSpot.CameraFileSelectionDialog.Run () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
  at FSpot.Core+ImportCommand.Execute () [0x00000] 
  at FSpot.Core.Import (System.String path) [0x00000] 
  at FSpot.Driver.Main (System.String[] args) [0x00000] 
.NET Version: 2.0.50727.42


Any news or fix to the problem ?

---

### Post by directhex on 2009-06-21
Try reporting the bug upstream

---

### Post by kroiz on 2009-06-21
> **directhex said:**
> Try reporting the bug upstream
What does that mean? how? please.

---

### Post by directhex on 2009-06-21
> **kroiz said:**
> What does that mean? how? please.

[http://bugzilla.gnome.org/enter_bug.cgi?product=f-spot](http://bugzilla.gnome.org/enter_bug.cgi?product=f-spot)

---

### Post by kroiz on 2009-06-21
> **directhex said:**
> [http://bugzilla.gnome.org/enter_bug.cgi?product=f-spot](http://bugzilla.gnome.org/enter_bug.cgi?product=f-spot)
why f-spot in the link?

---

### Post by directhex on 2009-06-22
> **kroiz said:**
> why f-spot in the link?

Because F-Spot is the photo management app, the one throwing your error?

---

### Post by kroiz on 2009-06-22
> **directhex said:**
> Because F-Spot is the photo management app, the one throwing your error?

I think it is more basic problem. it is not possible to mount the device.

for me the problem started after  upgrading to the last ubuntu I wonder if my fellow posters started getting the errors after the last upgrade?

yundo and libbresse when did the problem started for you?
can you access the camera card  on the camera via "open folder"?

---


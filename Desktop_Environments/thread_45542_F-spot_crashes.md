---
title: "F-spot crashes"
date: 2005-06-30
forum: Desktop Environments
---

### Post by szdavid on 2005-06-30
Hello,

when I double click on a picture in f-spot it crashes ; i have got this message in my console :
> 
    ** (f-spot:12994): WARNING **: Invalid borders specified for theme pixmap:
            /home/szdavid/.themes/MacOS-X/gtk-2.0/entry2.png,
    borders don't fit within the image

    ** (f-spot:12994): WARNING **: Missing method Write in assembly /usr/share/dotnet/f-spot/f-spot.exe, type PixbufLoader

    Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
    in <0x00000> <unknown method>
    in <0x00032> PixbufUtils:LoadAtMaxSize (System.String path, Int32 max_width, Int32 max_height)
    in <0x00034> PixbufLoader:ProcessRequest (.RequestItem request)
    in <0x00010> FSpot.ThumbnailGenerator:ProcessRequest (.RequestItem request)
    in <0x0012a> PixbufLoader:WorkerThread ()
    in (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

    ** (f-spot:12994): WARNING **: Missing method Write in assembly /usr/share/dotnet/f-spot/f-spot.exe, type PixbufLoader

    Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
    in <0x00000> <unknown method>
    in <0x00000> <unknown method>
    in (wrapper managed-to-native) Gtk.Application:gtk_main ()
    in <0x00007> Gtk.Application:Run ()
    in <0x00007> Gnome.Program:Run ()
    in <0x0014a> Driver:Main (System.String[] args)


What should i do ?
Merci

---

### Post by manicka on 2005-06-30
How did you install f-spot? 

I'm using 0.0.13 from backports and haven't had a problem

---

### Post by szdavid on 2005-06-30
[QUOTE=manicka]How did you install f-spot? 

I'm using 0.0.13 from backports and haven't had a problem[/QUOTE]
 I have got 0.0.12 but from synaptyc ; how to install the last version ?

---

### Post by manicka on 2005-07-06
add the backport repos to apt/synaptic

---

### Post by Majlo on 2005-07-06
[QUOTE=szdavid]I have got 0.0.12 but from synaptyc ; how to install the last version ?[/QUOTE]

Look at this 
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
Add backport repository , then 
*sudo apt-get update* 
*sudo apt-get upgrade*

---


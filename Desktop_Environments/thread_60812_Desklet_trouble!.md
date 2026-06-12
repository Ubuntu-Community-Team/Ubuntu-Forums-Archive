---
title: "Desklet trouble!"
date: 2005-08-29
forum: Desktop Environments
---

### Post by rama on 2005-08-29
I have installed the gDesklets deamon a while ago and every time it starts up I get the following error:

```
No Control could be found for interface IRun:0x3lu172654csufa4m25o2w7c
This means that a functionality won't be available during execution!
```

Of course this all started after I messed up with some of the desklets that I had installed. Since I dont remember what I did ( :roll: ) is there any way I could find out which Control/Interface is causing this and do something about it?

I checked the log and here is what I got:

```
Log messages of /home/jsar/.gdesklets/gdesklets:0.0.log                              
==========================================================[08/29/05-18:16:25]===     
Deprecation: Sensors are deprecated since v0.30.                                     
Please consider using controls and inline scripts.                                   
/usr/lib/python2.4/site-packages/gtk-2.0/gnome/vfs.py:4: DeprecationWarning: Module  
gnome.vfs is deprecated; please import gnomevfs instead                              
  DeprecationWarning)                                                                
==========================================================[08/29/05-18:16:25]===     
Adding "/home/jsar/.gdesklets/Displays/starterbar.display" with ID                   
"id11237848905612282" to the desklet list.                                           
==========================================================[08/29/05-18:16:26]===     
Warning: Couldn't read file                                                          
"/home/jsar/.gdesklets/Displays/SideStripes/gfx/memory/preview.png".                 
==========================================================[08/29/05-18:16:26]===     
Adding "/home/jsar/.gdesklets/Displays/SideStripes/memory.display" with ID           
"id1124209208615204" to the desklet list.                                            
/usr/lib/gdesklets/display/DisplayTarget.py:352: GtkWarning:                         
gtk_widget_set_size_request: assertion `width >= -1' failed                          
  self.get_widget().set_size_request(new_w.as_px(), new_h.as_px())                   
==========================================================[08/29/05-18:16:26]===     
Warning: Couldn't read file                                                          
"/home/jsar/.gdesklets/Displays/SideStripes/gfx/network/preview.png".                
==========================================================[08/29/05-18:16:27]===     
Adding "/home/jsar/.gdesklets/Displays/SideStripes/network.display" with ID          
"id11242092959052400" to the desklet list.                                           
==========================================================[08/29/05-18:16:27]===     
Warning: Couldn't read file "/home/jsar/.gdesklets/Displays/".                       
==========================================================[08/29/05-18:16:28]===     
Warning: Couldn't read file                                                          
"/home/jsar/.gdesklets/Displays/SideStripes/gfx/disk/preview.png".                   
==========================================================[08/29/05-18:16:28]===     
Adding "/home/jsar/.gdesklets/Displays/SideStripes/disk.display" with ID             
"id11242093980052345" to the desklet list.                                           
==========================================================[08/29/05-18:16:28]===     
Warning: Couldn't read file                                                          
"/home/jsar/.gdesklets/Displays/SideStripes/gfx/disk/preview.png".                   
==========================================================[08/29/05-18:16:28]===     
Adding "/home/jsar/.gdesklets/Displays/SideStripes/disk.display" with ID             
"id11242095085961290" to the desklet list.                                           
==========================================================[08/29/05-18:16:29]===     
Adding "/home/jsar/.gdesklets/Displays/SideStripes/cpu.display" with ID              
"id11242105538811228" to the desklet list.                                           
==========================================================[08/29/05-18:16:29]===     
Adding "/home/jsar/.gdesklets/Displays/SC-Weather/sc-weather.display" with ID        
"id11247534780638298" to the desklet list.                                           
Traceback (most recent call last):                                                   
  File "./YahooWeather2/__init__.py", line 56, in __update_weather_run               
  File "./YahooWeather2/__init__.py", line 68, in __parse_weather                    
AttributeError: 'NoneType' object has no attribute 'group'                           
None                                                                                 
==========================================================[08/29/05-18:16:49]===     
Deprecation: Please use new style call.                                              
/usr/lib/gdesklets/gdesklets-daemon:107: GtkDeprecationWarning: gtk.FALSE is         
deprecated, use False instead                                                        
  gtk.main()                                                                         
4[]                                                                                  
caption-color                                                                        
==========================================================[08/29/05-18:17:36]===     
Warning: Couldn't read file "/home/jsar/.gdesklets/Displays/".                       
==========================================================[08/29/05-18:17:43]===     
Warning: Couldn't read file "/home/jsar/.gdesklets/Displays/".                       
5[]                                                                                  
==========================================================[08/29/05-18:18:57]===     
Warning: Couldn't read file "/home/jsar/.gdesklets/Displays/".                       
==========================================================[08/29/05-18:19:10]===     
Warning: Couldn't read file "/home/jsar/.gdesklets/Displays/".                       
4[]                                                                                  

```

Quite a mess ...

---

### Post by KingBahamut on 2005-08-29
apt-get remove gdesklets gdesklets-data 

then

rm /home/<username>/.gdesklets/ -fr 

apt-get install gdesklets 

this of course will utterly uninstall gdesklets and reinstall them, but it should remove the suspect control sets you dont have.

---

### Post by rama on 2005-08-29
[QUOTE=KingBahamut]apt-get remove gdesklets gdesklets-data 

then

rm /home/<username>/.gdesklets/ -fr 

apt-get install gdesklets 

this of course will utterly uninstall gdesklets and reinstall them, but it should remove the suspect control sets you dont have.[/QUOTE]
 Can I backup my settings and then just reinstall the desklets I use? Or does the applet create new random ids like "id11242093980052345" every time I install a desklet? 
But then again I guess this will propably restore the problem as well as my settings right?

---

### Post by KingBahamut on 2005-08-29
correct to the last question.

---

### Post by sweetthdevil on 2005-09-01
hi, i've got the same probleme, and i find it as well, in the french forum, and the gdesklets forum...

everytime it's exactly the same error message (same code as well)...

I tried to uninstall it, and reinstall it, but the probleme came back.

Any idee what to do, it's not to much trouble, but when i want to show ubuntu, the so great linux distribution, i've got this error message...

not so great  :roll:

---

### Post by rama on 2005-09-03
[QUOTE=sweetthdevil]hi, i've got the same probleme, and i find it as well, in the french forum, and the gdesklets forum...

everytime it's exactly the same error message (same code as well)...

I tried to uninstall it, and reinstall it, but the probleme came back.

Any idee what to do, it's not to much trouble, but when i want to show ubuntu, the so great linux distribution, i've got this error message...

not so great  :roll:[/QUOTE]
 Sorry sweetthdevil ... no luck so far. I uninstalled the deamon along with the settings as KingBahamut suggested. But I didn't reinstall the deamon. I decided not to use it any more.
But I was browsing the options the Configurator Editor has and I noticed that there is a section for gDesklets under "apps" ... 
First of all why does that still exist? 
and how can I remove it?

---

### Post by sweetthdevil on 2005-09-08
I actualy find out wich gdesklets is causing to error, it's the SideStripes desklet (v0.3) the sidebar network display.

I don't know why, but if someone can look at it, it'll be great  \\:D/

---

### Post by rama on 2005-09-09
[QUOTE=sweetthdevil]I actualy find out wich gdesklets is causing to error, it's the SideStripes desklet (v0.3) the sidebar network display.

I don't know why, but if someone can look at it, it'll be great  \\:D/[/QUOTE]
 I cant verify that cause I dont have gDesklets installed anymore but I can say that I also used that desklet.

---


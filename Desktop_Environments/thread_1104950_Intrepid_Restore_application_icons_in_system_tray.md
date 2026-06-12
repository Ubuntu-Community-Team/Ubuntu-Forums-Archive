---
title: "Intrepid: Restore application icons in system tray"
date: 2009-03-24
forum: Desktop Environments
---

### Post by mibadt on 2009-03-24
Hi,
I'm on a fully updated Kubuntu Intrepid (8.10).
Some how all the icons of my applications (e.g., kmail, firefox) disappeared from the system tray.

Enclosed please find my ~/.kde/share/config/plasma-appletsrc file as I guess I'll have to edit it.

Thanks up front
Michael Badt
-------------------my plasma-appletsrc-------------
[Containments][1]                                                                                                                        
activity=                                                                                                                                
desktop=-1                                                                                                                               
formfactor=0                                                                                                                             
geometry=0,0,1680,1050                                                                                                                   
immutability=1                                                                                                                           
location=0                                                                                                                               
plugin=desktop                                                                                                                           
screen=0                                                                                                                                 
wallpaperplugin=image                                                                                                                    
wallpaperpluginmode=SingleImage                                                                                                          
zvalue=0                                                                                                                                 

[Containments][1][Applets][13]
geometry[$d]                  
immutability[$d]              
plugin[$d]                    
zvalue[$d]                    

[Containments][1][Applets][13][Configuration]
autoSave[$d]                                 

[Containments][1][Applets][2]
formfactor[$d]               
geometry[$d]                 
immutability[$d]             
location[$d]                 
plugin[$d]                   
screen[$d]                   
zvalue[$d]                   

[Containments][1][Applets][2][Configuration]
url[$d]                                     

[Containments][1][Wallpaper][image]
slideTimer=600                     
slidepaths=/usr/share/wallpapers/  
userswallpapers=                   
wallpaper=/home/miki/.kde/share/wallpapers/Icestorm-1.0-0.png
wallpapercolor=56,111,150                                    
wallpaperposition=0                                          

[Containments][3]
activity=        
desktop=-1       
formfactor=2     
geometry=0,-44,1280,38
immutability=1        
location=4            
plugin=panel          
screen=0              
zvalue=150            

[Containments][3][Applets][10]
geometry=1222,6,32,32         
immutability=1                
plugin=trash                  
zvalue=0                      

[Containments][3][Applets][11]
geometry=36,6,32,32           
immutability=1                
plugin=quickaccess            
zvalue=0                      

[Containments][3][Applets][12]
geometry=1068,6,50,32         
immutability=1                
plugin=                       
zvalue=0                      

[Containments][3][Applets][4]
geometry=0,6,32,32           
immutability=1               
plugin=launcher              
zvalue=0                     

[Containments][3][Applets][4][Shortcuts]
global=                                 

[Containments][3][Applets][5]
geometry=956.954248366013,6,32,32
immutability=1                   
plugin=notifier                  
zvalue=0                         

[Containments][3][Applets][6]
geometry=72,6,26,32          
immutability=1               
plugin=pager                 
zvalue=0                     

[Containments][3][Applets][7]
geometry[$d]
immutability[$d]
plugin[$d]
zvalue[$d]

[Containments][3][Applets][8]
geometry=102,6,850.954248366013,32
immutability=1
plugin=systemtray
zvalue=0

[Containments][3][Applets][8][Configuration][PopupApplet]
DialogHeight=72
DialogWidth=200

[Containments][3][Applets][9]
geometry=992.954248366013,6,225.045751633987,32
immutability=1
plugin=digital-clock
zvalue=1

[Containments][3][Applets][9][Configuration][ExtenderItems][1]
extenderIconName=view-pim-calendar
extenderItemName=calendar
extenderTitle=Calendar
sourceAppletId=9
sourceAppletPluginName=digital-clock

[Containments][3][Applets][9][Configuration][PopupApplet]
DialogHeight=268
DialogWidth=250

[Containments][3][Configuration]
maximumSize=1680,38
minimumSize=1280,38

[General]
immutability=1

---

### Post by Monsieur Gonzalez on 2009-03-24
Which KDE version?

---

### Post by mibadt on 2009-03-24
Hi,

That's KDE 4.2.00

Michael Badt

---


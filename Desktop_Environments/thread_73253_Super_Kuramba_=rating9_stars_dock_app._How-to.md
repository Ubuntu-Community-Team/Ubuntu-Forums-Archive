---
title: "Super Kuramba =rating:9 stars dock app. :How-to"
date: 2005-10-08
forum: Desktop Environments
---

### Post by Omnios on 2005-10-08
First off for KDE  users Kurumba might not be number one in eye candy though some real sweet apps are out there. I would  recomend it for anyone who wants some fuctional eye candy but do not want to put a large load on the system.

 Most Super  Kurumba apps are very light on resources "included example is about 6% cpu and less than 5 megs ram including the Super Kuramba program and expecialy the ones with the standart sensor arrangements cpu, temp, Ram, Net. There is also apps that use sensor= program but counting on the refresh time they can run at about 25% cpu load. Basicly  think the simpler the graphics the lower the load.

Edit:Notes:
 Basicly with Kuramba aand Super Kuramba you download  the tar.gz and unzip it into a File  you create to hold all your Karumba themes. Then run Kuramba/Super Kuramba and chose the file you want to run xxxxx.theme.

 A few tricks  you may have to modify the file to work with your systems. 

 In run terminal and type sensors the  out put will be what your system is using ex mine  uses  M/B for  mother board temp which is different from what most of the apps  use. Now right click the Kurumba app and chose edit / edit theme. Now you will have to go through the theme file and find what you have to change which is usualy in <group> sections. What you are looking for starts with sensor=sensor type=#### the type part is what you are looking for to change and there is usualy a few entrys  pertainging to Text/Bar/Graph entrys. The same holds   true for network where you haave ppp0 and eth0 where you maay have to change the type pertaing to what your net is set up as. I would recomend reading the Super Karambe creation page "Link Above" to understand more of how it works. 

This is the second system sensor I made Im thinking of making one for a lap top that is a very thin bar but Ill think of that for a few days.



 [IMG]http://ubuntuforums.org/gallery/files/1/4/1/2/6/Senses.jpg[/IMG]

 Super  Karamba is realy easy to script and learn how to script. Probaly easier than leaarning html. The hard part Kurumba uses a x=0 y=0 for layout wwhich takes a while to get used to but in no time you will be placing components pretty dam close to where they are supposed to go. Tip : with app running edit in text editor change the x y to what you think they should go then save with the save icon and refload the app. Your new x y  placement will show up.



[[HTML]Super Kuramba How to files[/HTML]]("http://netdragon.sourceforge.net/sinfo.html")



```

# Icons what icons ment to run light.
# Based on sensor references from varios sensors.

# Start 
# General

karamba x=100 y=200 w=215 h=255 interval=600 locked=false
defaultfont font="malayalam" fontsize=10 color=0,0,0 align="left
Image X=0 y=0 path="img/background.png"

<group>
       #Top Graph CPU/Ram

       graph x=50 y=17 w=150 h=69 points=60 color=130,26,30 sensor=memory format="%um" interval=900 max="%tm"
       graph x=50 y=17 w=150 h=69 points=60 color=132,10,74 sensor=memory format="%umb" interval=900 max="%tm"
       graph x=50 y=17 w=150 h=69 points=60 color=255,0,0 sensor=cpu interval=900 max=100
       

        #Top Graph Graphics 
       image x=1 y=18 path="img/leftbar.png" 
       image x=49 y=18 path="img/graphbar.png"
       image x=203 y=18 path="img/graphbar.png"
       image x=49 y=89 path="img/graphbottom.png"
<group>

       #CPU info

       image x=1 y=18 path="img/graphbar.png" 
       image x=49 y=18 path="img/graphbar.png"
       image x=204 y=18 path="img/graphbar.png"
       image x=49 y=88 path="img/graphbottom.png"
       text x=4 y=2 sensor=program program="cat /proc/cpuinfo | grep 'model name' | sed -e 's/.*: //'" fontsize=12
       text x=47 y=30 sensor=cpu format="%v%" align="right" interval=900 color=255,0,0 fontsize=16
       text x=11 y=17 value="CPU :"color=0,0,0 fontsize=11
       
       bar   x=200 y=19 w=2 h=69 vertical=true sensor=cpu type="cpu"  path="img/bargraph.png" min=0 max=100 interval=600
       
      
</group>

<group>

       #Memory usage. 

       image x=6 y=75 path="img/rambar.png"
       
       text x=4 y=49 value="RAM/MB" color=0,0,0 fontsize=11
       text x=47 y=60 sensor=memory format="%umb"align="right" interval=1000 color=132,10,74 fontsize=14
       text x=47 y=78 sensor=memory format="%tm"align="right" interval=1000 color=132,10,74 fontsize=14
       text x=5 y=95 sensor=memory format="RAM+Cach=%um :" color=130,26,30 interval=4000 color=0,0,0 fontsize=12
       text x=110 y=95 sensor=memory format="Swap %us/%ts MB" interval=4000 color=0,0,0 fontsize=12
</group>


<group> 

       # Graph/temp divider
       image x=5 y=110 path="img/divider.png"

       # cpu temp, MB temp bars, + fans rrpm

       text x=5 y=115 value="CPU Temp" color=0,0,0 fontsize=12
       image x=5 y=131 path="img/bartop.png"
       image x=75 y=131 path="img/endbar.png"
       bar   x=5 y=132 w=70 h=4 vertical=false sensor=sensor type="CPU Temp" format="%v" path="img/bar1.png" min=0 max=50 interval=2000
       
       text x=5 y=141 sensor=sensor type="CPU Temp" format="%v *c"color=100,250,50 fontsize=18 interval=2500
       text x=5 y=162 sensor=sensor type="fan1" format="%v rpm" fontsize=12 interval=2500
       image x=63 y=163 path="img/fanbulbr.png"
       bar x=63 y=163 w=8 h=8 vertical=false sensor=sensor type="fan1" format="%v" path="img/fanbulb.png" min=1 max=2
        
       #temp divider#
       image x=5 y=178 path="img/bartop.png"
      

       #MB temp bar+graphics

       #temp side bars
       image x=1 y=115 path="img/leftbar2.png"
       image x=79 y=115 path="img/leftbar2.png"
       image x=204 y=115 path="img/leftbar2.png"

       image x=5 y=200 path="img/bartop.png"
       image x=75 y=200 path="img/endbar.png"
       bar x=5 y=201 w=70 h=4 vertical=false sensor=sensor type="M/B Temp" format="%v" path="img/bar1.png" min=0 max=50 interval=2000


     
       text x=5 y=184 value="MB Temp" color=0,0,0 fontsize=12
       text x=5 y=210 sensor=sensor type="M/B Temp" format="%v.0 *c" color=100,250,50 fontsize=18 interval=2500
       text x=5 y=231 sensor=sensor type="fan2" format="%v rpm" fontsize=12 interval=2500
       image x=63 y=232 path="img/fanbulbr.png"
       bar x=63 y=232 w=8 h=8 vertical=false sensor=sensor type="fan2" format="%v" path="img/fanbulb.png" min=1 max=2
       
      
      
</group>      

<group>
       
       #Net monitor graphs

       image x=82 y=167 path="img/netbot.png" 
       graph x=82 y=115 w=119 h=50 points=30 color=247,235,214  sensor=network format="%out" interval=1200 MAX=50
       graph x=82 y=115 w=119 h=50 points=30 color=100,250,50  sensor=network format="%in" interval=1200 max=50
       
       text x=100 y=185 sensor=network format="in  :%in kbs" align="left"  interval=900  fontsize=18 color=100,250,50
       image x=85 y=193 path="img/fanbulbr.png"
       bar x=85 y=193 w=8 h=8 vertical=false sensor=network type="%in" format="%in" path="img/fanbulb.png" min=1 max=2

       text x=100 y=215 sensor=network format="out:%out kbs" align="left"  interval=900  fontsize=18 color=255,255,0
       image x=85 y=223 path="img/fanbulbr.png"
       bar x=85 y=223 w=8 h=8 vertical=false sensor=network type="%out" format="%out" path="img/fanbulb.png" min=1 max=2

</group>
 
```

 Anyways Kuramba  is fun at the least.

---


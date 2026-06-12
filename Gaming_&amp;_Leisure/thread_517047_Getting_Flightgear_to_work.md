---
title: "Getting Flightgear to work"
date: 2007-08-04
forum: Gaming &amp; Leisure
---

### Post by storky on 2007-08-04
there are several old threads of people recieving an error in there terminal when they try to run flightgear. The error usually has something to do with the program not being able to find autosave.xml in a .fgfs inside there user folder, both of wich dont exist. I was wondering if anyone has got around this issue,

Error reading properties: 
Failed to open file
 at /home/shaun/.fgfs/autosave.xml
 (reported by SimGear XML Parser)
DRM_I830_CMDBUFFER: -22

---

### Post by buckrodgers on 2007-08-12
On feisty it did install and run with out problems 

 here is an example of my autosave.xml if this is of any help

```

<?xml version="1.0"?>

<PropertyList>
  <sim>
    <startup>
      <save-on-exit>true</save-on-exit>
    </startup>
    <sound>
      <volume type="float">0.8</volume>
      <atc-chatter type="bool">false</atc-chatter>
    </sound>
    <rendering>
      <horizon-effect type="bool">false</horizon-effect>
      <enhanced-lighting type="bool">false</enhanced-lighting>
      <distance-attenuation type="bool">false</distance-attenuation>
      <static-lod>
        <detailed>1500</detailed>
        <rough>9000</rough>
        <bare>30000</bare>
      </static-lod>
      <random-objects type="bool">true</random-objects>
      <precipitation-enable type="bool">false</precipitation-enable>
      <lightning-enable type="bool">false</lightning-enable>
      <bump-mapping type="bool">false</bump-mapping>
      <clouds3d-enable type="bool">false</clouds3d-enable>
      <clouds3d-vis-range type="float">25000</clouds3d-vis-range>
      <clouds3d-density type="float">100</clouds3d-density>
      <clouds3d-cache-size type="int">1024</clouds3d-cache-size>
      <clouds3d-cache-resolution type="int">64</clouds3d-cache-resolution>
      <shadows-ac type="bool">false</shadows-ac>
      <shadows-ac-transp type="bool">false</shadows-ac-transp>
      <shadows-ai type="bool">false</shadows-ai>
      <shadows-to type="bool">false</shadows-to>
      <shadows-debug type="bool">false</shadows-debug>
      <fps-display type="bool">false</fps-display>
    </rendering>
    <menubar>
      <visibility type="bool">true</visibility>
    </menubar>
    <gui>
      <current-style type="int">0</current-style>
    </gui>
    <ai-traffic>
      <enabled type="bool">false</enabled>
      <level type="int">1</level>
    </ai-traffic>
  </sim>
</PropertyList>

```

---

### Post by storky on 2007-08-12
i tried making an autosave.xml file with that exact text in it, and now i get 

DRM_I830_CMDBUFFER: -22
DRM_I830_CMDBUFFER: -22
DRM_I830_CMDBUFFER: -22

in the terminal when i try to run it...how did u do your install? from the repositories or from source?

im running fiesty to

---


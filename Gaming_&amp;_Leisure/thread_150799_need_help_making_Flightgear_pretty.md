---
title: "need help making Flightgear pretty"
date: 2006-03-26
forum: Gaming &amp; Leisure
---

### Post by ndhskp on 2006-03-26
I'm using Dapper and a Intel 3.2E GHz with 2GB ram and a Nvidia 6600GT card with Flightgear Version 0.9.10-pre2 and SimGear-0.3.10-pre2.  When I run Flightgear I get any where from 50 to over 100 fps.  I want to increase the level of visual quality so that I'm only getting about 20 to 30 fps.  When I'm flying the ground only shows up in squre'ish chunks and the view distance is very short.

1.  I want the ground and sky to extend all the way to the horizon as far as you can see for a given altitude.  I have orded the 3 DVD's of the terrain but I should point out that lack of terrain is not the problem with the terrain chunking.

2.  I want the details cranked to the max.

3.  Where are the other planes in the sky?  Meaning where's the AI ground and sky traffic visually, I can hear the ATC chatter but I don't see them.

4.  What can I do to make the aircraft more real.

My current settings in **preferences.xml** are: (I've only included revelent portions)
```
<xsize type="int">1024</xsize>
<ysize type="int">768</ysize>
<game-mode type="bool">true</game-mode>
<fullscreen type="bool">true</fullscreen>
<static-lod>
<detailed userarchive="y">30000</detailed>
<rough userarchive="y">60000</rough>
<bare userarchive="y">90000</bare>
<random-objects type="bool" userarchive="y">true</random-objects>
<horizon-effect type="bool" userarchive="y">true</horizon-effect>
<enhanced-lighting type="bool" userarchive="y">true</enhanced-lighting>
<distance-attenuation type="bool" userarchive="y">true</distance-attenuation>
<precipitation-enable type="bool" userarchive="y">false</precipitation-enable>
<lightning-enable type="bool" userarchive="y">false</lightning-enable>
<bump-mapping type="bool" userarchive="y">true</bump-mapping>
<clouds3d-enable type="bool" userarchive="y">true</clouds3d-enable>
<clouds3d-vis-range type="float" userarchive="y">25000</clouds3d-vis-range>
<clouds3d-density type="float" userarchive="y">100</clouds3d-density>
<clouds3d-cache-size type="int" userarchive="y">1024</clouds3d-cache-size>
<clouds3d-cache-resolution type="int" userarchive="y">128</clouds3d-cache-resolution>
<draw-otw type="bool">true</draw-otw>
<shadows-ac type="bool" userarchive="y">true</shadows-ac>
<shadows-ac-transp type="bool" userarchive="y">true
</shadows-ac-transp>
<shadows-ai type="bool" userarchive="y">true</shadows-ai>
<shadows-to type="bool" userarchive="y">true</shadows-to>
<shadows-debug type="bool" userarchive="y">false</shadows-debug>
<fps-display type="bool" userarchive="y">true</fps-display>
<realism>10</realism>
```

---


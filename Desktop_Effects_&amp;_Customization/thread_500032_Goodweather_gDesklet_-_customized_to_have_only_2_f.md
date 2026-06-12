---
title: "Goodweather gDesklet - customized to have only 2 forecasts?"
date: 2007-07-13
forum: Desktop Effects &amp; Customization
---

### Post by tak1150 on 2007-07-13
Hi,

I couldn't find a thread to address this specific issue.

I read somewhere that you can customize goodweather to display less than 5 forecasts (by default it shows 5 forecasts). I only want it to show 2 or 3. How can this be achieved? Thank you!

---

### Post by mike102282 on 2007-07-13
> **tak1150 said:**
> Hi,

I couldn't find a thread to address this specific issue.

I read somewhere that you can customize goodweather to display less than 5 forecasts (by default it shows 5 forecasts). I only want it to show 2 or 3. How can this be achieved? Thank you!
 

I just right click on it and select configure and go from there.

---

### Post by tak1150 on 2007-07-13
Thanks for replying.

But there is no option for limiting the # of forecast displays in the configuration window.

---

### Post by tak1150 on 2007-07-13
Well, thanks for the simple advice of right clicking.
I saw the option for "View Source" and saw how similar the source is to HTML.

So I figured I could mess with it. So I did.

First make a copy of the config file.
```
cd .gdeskelts/Displays/GoodWeather
cp GoodWeather.display GoodWeather.display.backup
```

Then edit the file. To be lazy, I'll just post the edited file and you can use it if you like.
So open the file.
gedit GoodWeather.display
And delete the content and paste this.
```
<?xml version="1.0" encoding="UTF-8"?>

<display window-flags="below, sticky" anchor="ne">
  <meta author="Konrad Rieck"
        name="GoodWeather display"
        version="0.3"
        description="Themable weather condition and forecast display (needs FontSelector)"/>

  <sensor id="w" module="GoodWeather"/>
  <sensor id="f" module="FontSelector,3,Sans bold 14,white,Sans 8,white, Sans 8,white"/>

  <!-- left and right border -->
  <image relative-to="grp,x" uri="gfx/bg-right.png"/>
  <image id="left" x="16" y="16" uri="gfx/bg-left.png"/>

  <!-- background -->
  <group id="grp" relative-to="left,x" bg-uri="gfx/bg-weather.png">
    <group width="1" height="80"/>

    <!-- current conditions -->
    <label id="t" x="60" y="29" anchor="sw"
           watch="value=w:temperature, color=f:color0, font=f:font0" />
    <label id="l1" relative-to="t, y" y="-4"
           watch="value=w:label1, color=f:color1, font=f:font1" />
    <label id="l2" relative-to="l1, y" y="-2" 
           watch="value=w:label2, color=f:color1, font=f:font1" />
    <label id="l3" relative-to="l2, y" y="-2" 
           watch="value=w:label3, color=f:color1, font=f:font1" />

    <!-- forecasts -->
    <label id="d0" x="150" y="10"
           watch="value=w:day0, color=f:color2, font=f:font2" />
    <image relative-to="d0, y" x="-5" y="-5" uri="gfx/bg-bar.png" />
    <image relative-to="d0, y" y="-2" watch="uri=w:icon0" />
    <label relative-to="d0, y" y="24"
           watch="value=w:temp0, color=f:color2, font=f:font2" />

    <label id="d1" relative-to="d0, x" x="30" 
           watch="value=w:day1, color=f:color2, font=f:font2" />
    <image relative-to="d1, y" x="-5" y="-5" uri="gfx/bg-bar.png" />
    <image relative-to="d1, y" y="-2" watch="uri=w:icon1" />
    <label relative-to="d1, y" y="24" 
           watch="value=w:temp1, color=f:color2, font=f:font2" />

    <label id="d2" relative-to="d1, x" x="30" 
           watch="value=w:day2, color=f:color2, font=f:font2" />
    <image relative-to="d2, y" x="-5" y="-5" uri="gfx/bg-bar.png" />
    <image relative-to="d2, y" y="-2" watch="uri=w:icon2" />
    <label relative-to="d2, y" y="24" 
           watch="value=w:temp2, color=f:color2, font=f:font2" />


    <label relative-to="d2, x" x="15" value=" " />
  </group>

  <image id="icon" y="5" x="8" width="80" watch="uri=w:icon"/>
</display>
```

I have also edited it so that the letters don't overlap for the 1st and 2nd forecasts.
Yahoo!

---


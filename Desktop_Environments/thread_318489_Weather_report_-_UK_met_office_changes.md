---
title: "Weather report - UK met office changes"
date: 2006-12-14
forum: Desktop Environments
---

### Post by markwren on 2006-12-14
Since end Nov the Gnome Weather Report applet has failed to show me a local UK forecast.
As the "radar map" was also suddenly failing to load from my custom setting on [www.metoffice.com](www.metoffice.com) I went to look there first. 

I discovered that the UK metoffice website has been substantially reorganised. Sadly for me there is no longer a "latest" satellite image I can use for the radar map - only images with hard-set names containing the date and time.

As both map and forecast started to fail simultaneously, I suspect that the metoffice site reorganisation is also the cause of my losing a local weather forecast for Exeter, UK.

I have reset my custom map to [http://image.weather.com/images/sat/uksat_600x405.jpg](http://image.weather.com/images/sat/uksat_600x405.jpg) for now. Any suggestions for somewhere better?

But I cannot find a way to redirect the forecast. Any ideas?

Mark

---

### Post by chrisccoulson on 2006-12-14
Hi,

I also have this problem. There is another thread [here]("http://www.ubuntuforums.org/showthread.php?t=313007")

Sorry, but I don't have any ideas at the moment :(

---

### Post by tabascoterrier on 2008-03-24
I knocked up a quick PHP wrapper to get round this - I point my weather applet at my local machine, [http://localhost/radar.php](http://localhost/radar.php), which redirects to the latest image on the Met Office site.

[PHP]
<?php
// redirect browser to the latest Met Office radar map
$date = (date("i") < 30) ? date("YmdH00") : date("YmdH30");
$imageURI = 'http://www.metoffice.gov.uk/weather/images/uk_britradar_' . $date . '.gif';
header("Location: $imageURI");
?>
[/PHP]

---


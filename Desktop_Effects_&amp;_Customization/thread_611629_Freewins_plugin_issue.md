---
title: "Freewins plugin issue"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by canceLinux on 2007-11-13
hi.. i've installed the "freewins plugin" in fusion. its look like working, but i can't set an initialize button for it, how can i do? or is there anybody using freewins, can you send me your xml ( or whatever needed) files..
i've tried gconf &flat file and restarted compiz but no success..:confused:
thanks for answers..

---

### Post by fuchur on 2007-12-01
see my post of today in the howto thread. it might help

---

### Post by macaholic on 2007-12-01
This is my xml file:
```
<?xml version="1.0" encoding="UTF-8"?>
<compiz>
    <plugin name="freewins">
	<short>Freewins</short>
	<long>Freely rotate windows</long>
	<display>
	    <option type="button" name="initiate_button">
			<short>Initiate rotation</short>
			<long>Start Rotation</long>
			<default>&lt;Control&gt;&lt;Shift&gt;Button1</default>
	    </option>
	    <option type="button" name="reset_button">
			<short>Reset</short>
			<long>Reset Rotation</long>
			<default>&lt;Control&gt;&lt;Shift&gt;Button2</default>
	    </option>
	    <option type="key" name="toggle_axis">
			<short>Axis help toggle</short>
			<long>Axis selection helper </long>
			<default>&lt;Control&gt;&lt;Shift&gt;a</default>
	    </option>
	</display>
    </plugin>
</compiz>
```

---

### Post by fuchur on 2007-12-01
that's interesting. originally i had the same xml file as macaholic, but it does not work for me...

the modifications that make it work i posted in this thread: 
[http://ubuntuforums.org/showthread.php?t=602062&page=2&highlight=freewins](http://ubuntuforums.org/showthread.php?t=602062&page=2&highlight=freewins)

---


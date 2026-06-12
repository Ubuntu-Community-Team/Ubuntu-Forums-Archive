---
title: "[ ignore ] testing forum code"
date: 2007-07-01
forum: Forum Feedback &amp; Help
---

### Post by Average_Joe on 2007-07-01
Please ignore - I am using this thread only to test and learn some more about the forum posting codes used here.  THANKS!!

----
Test 1
----

</div>Hi and welcome, it gives you the command to use in the terminal  to view your xorg file <br />
<div style="margin:20px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px">PHP Code:</div>

	<div class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 34px;
		text-align: left;
		overflow: auto">
		<code style="white-space:nowrap">
			<!-- php buffer start --><code><span style="color: #000000">
<span style="color: #0000BB">sudo&nbsp;nano&nbsp;</span><span style="color: #007700">/</span><span style="color: #0000BB">etc</span><span style="color: #007700">/</span><span style="color: #0000BB">X11</span><span style="color: #007700">/</span><span style="color: #0000BB">xorg</span><span style="color: #007700">.</span><span style="color: #0000BB">conf&nbsp;

<br /></span>
</span>
</code><!-- php buffer end -->
		</code>
	</div>
</div>However I would recommend using <br />
<div style="margin:20px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px">PHP Code:</div>
	<div class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 34px;
		text-align: left;
		overflow: auto">
		<code style="white-space:nowrap">

			<!-- php buffer start --><code><span style="color: #000000">
<span style="color: #0000BB">gksudo&nbsp;gedit&nbsp;</span><span style="color: #007700">/</span><span style="color: #0000BB">etc</span><span style="color: #007700">/</span><span style="color: #0000BB">X11</span><span style="color: #007700">/</span><span style="color: #0000BB">xorg</span><span style="color: #007700">.</span><span style="color: #0000BB">conf&nbsp;
<br /></span>
</span>
</code><!-- php buffer end -->
		</code>

	</div>
</div>If you scroll down to the devices section you should see your graphics card name there and be low it will be the driver then the screen section below it will have the resolution. <br />
For example here is mine.<br />
<div style="margin:20px; margin-top:5px">
	<div class="smallfont" style="margin-bottom:2px">PHP Code:</div>
	<div class="alt2" dir="ltr" style="
		margin: 0px;
		padding: 6px;
		border: 1px inset;
		width: 640px;
		height: 498px;
		text-align: left;
		overflow: auto">
		<code style="white-space:nowrap">
			<!-- php buffer start --><code><span style="color: #000000">
<span style="color: #0000BB">Section&nbsp;</span><span style="color: #DD0000">"Device"

<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Identifier&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"Intel&nbsp;Corporation&nbsp;Mobile&nbsp;945GM/GMS/940GML&nbsp;Express&nbsp;Integrated&nbsp;Graphics&nbsp;Controller"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Driver&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"i810"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">BusID&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"PCI:0:2:0"
<br /></span><span style="color: #0000BB">EndSection
<br />
<br />Section&nbsp;</span><span style="color: #DD0000">"Monitor"

<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Identifier&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"Generic&nbsp;Monitor"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Option&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"DPMS"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">HorizSync&nbsp;&nbsp;&nbsp;&nbsp;28</span><span style="color: #007700">-</span><span style="color: #0000BB">64
<br />&nbsp;&nbsp;&nbsp;&nbsp;VertRefresh&nbsp;&nbsp;&nbsp;&nbsp;43</span><span style="color: #007700">-</span><span style="color: #0000BB">60
<br />EndSection
<br />
<br />Section&nbsp;</span><span style="color: #DD0000">"Screen"

<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Identifier&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"Default&nbsp;Screen"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Device&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"Intel&nbsp;Corporation&nbsp;Mobile&nbsp;945GM/GMS/940GML&nbsp;Express&nbsp;Integrated&nbsp;Graphics&nbsp;Controller"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Monitor&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"Generic&nbsp;Monitor"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">DefaultDepth&nbsp;&nbsp;&nbsp;&nbsp;24

<br />&nbsp;&nbsp;&nbsp;&nbsp;SubSection&nbsp;</span><span style="color: #DD0000">"Display"
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Depth&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;1
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"1280x800"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">EndSubSection
<br />&nbsp;&nbsp;&nbsp;&nbsp;SubSection&nbsp;</span><span style="color: #DD0000">"Display"
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Depth&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;4
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"1280x800"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">EndSubSection
<br />&nbsp;&nbsp;&nbsp;&nbsp;SubSection&nbsp;</span><span style="color: #DD0000">"Display"
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Depth&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;8

<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"1280x800"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">EndSubSection
<br />&nbsp;&nbsp;&nbsp;&nbsp;SubSection&nbsp;</span><span style="color: #DD0000">"Display"
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Depth&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;15
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"1280x800"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">EndSubSection
<br />&nbsp;&nbsp;&nbsp;&nbsp;SubSection&nbsp;</span><span style="color: #DD0000">"Display"
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Depth&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;16
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"1280x800"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">EndSubSection

<br />&nbsp;&nbsp;&nbsp;&nbsp;SubSection&nbsp;</span><span style="color: #DD0000">"Display"
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">Depth&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;24
<br />&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Modes&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #DD0000">"1280x800"
<br />&nbsp;&nbsp;&nbsp;&nbsp;</span><span style="color: #0000BB">EndSubSection
<br />EndSection&nbsp;
<br /></span>
</span>
</code><!-- php buffer end -->
		</code>
	</div>

---

### Post by Average_Joe on 2007-07-01
---
Test 2
---

<div style="margin:20px; margin-top:5px">
<div class="smallfont" style="margin-bottom:2px">PHP Code:</div>
<div class="alt2" dir="ltr" style="
margin: 0px;
padding: 6px;
border: 1px inset;
width: 640px;
height: 498px;
text-align: left;
overflow: auto">
<code style="white-space:nowrap">
<!-- php buffer start --><code><span style="color: #000000">
<span style="color: #0000BB">Section&nbsp;</span><span style="color: #DD0000">"Device"

---

### Post by Average_Joe on 2007-07-01
---
Test 3
---

> wrap wrap wrap

---

### Post by Average_Joe on 2007-07-01
---
Test 4
---

[HTML]<div style="margin:20px; margin-top:5px">
<div class="smallfont" style="margin-bottom:2px">PHP Code:</div>
<div class="alt2" dir="ltr" style="
margin: 0px;
padding: 6px;
border: 1px inset;
width: 640px;
height: 498px;
text-align: left;
overflow: auto">
<code style="white-space:nowrap">
<!-- php buffer start --><code><span style="color: #000000">
<span style="color: #0000BB">Section&nbsp;</span><span style="color: #DD0000">"Device"[/HTML]

---

### Post by Average_Joe on 2007-07-01
---
Test 5
---

[PHP]<div style="margin:20px; margin-top:5px">
<div class="smallfont" style="margin-bottom:2px">PHP Code:</div>
<div class="alt2" dir="ltr" style="
margin: 0px;
padding: 6px;
border: 1px inset;
width: 640px;
height: 498px;
text-align: left;
overflow: auto">
<code style="white-space:nowrap">
<!-- php buffer start --><code><span style="color: #000000">
<span style="color: #0000BB">Section&nbsp;</span><span style="color: #DD0000">"Device"[/PHP]

---


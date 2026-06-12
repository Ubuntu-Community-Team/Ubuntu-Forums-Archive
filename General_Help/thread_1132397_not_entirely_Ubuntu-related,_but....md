---
title: "not entirely Ubuntu-related, but..."
date: 2009-04-21
forum: General Help
---

### Post by harmsc12 on 2009-04-21
Since any Ubuntu questions I have can usually be answered with the search tool, I'd like to pick your brains on the subject of my mother's website, where she is going to sell shawl pins, stitch markers, etc.
The site shows up just fine on IE, but the background color is gone completely in Firefox.

[http://artisticcharms.com]("http://artisticcharms.com")
There's the link, if anyone thinks they want to solve this riddle.

---

### Post by codeseer on 2009-04-21
A lot of the content is local linked.

```

<link rel="stylesheet" href="**file:///C|/Users/CHarms/Documents/artisticcharms/index.php_files/style.css**" type="text/css">
<link rel="stylesheet" href="file:///C|/Users/CHarms/Documents/artisticcharms/index.php_files/Verdana.css" type="text/css">
<link rel="stylesheet" href="file:///C|/Users/CHarms/Documents/artisticcharms/index.php_files/1f328cc69dd2c68c5cb9f2630e58328e.css" type="text/css">


<script language="JavaScript" type="text/javascript" src="file:///C|/Users/CHarms/Documents/artisticcharms/index.php_files/rvsnavigator.js"></script>


<script language="JavaScript" type="text/javascript" src="file:///C|/Users/CHarms/Documents/artisticcharms/index.php_files/layersmenu-library.js"></script>
<script language="JavaScript" type="text/javascript" src="file:///C|/Users/CHarms/Documents/artisticcharms/index.php_files/layersmenu.js"></script>

<script language="JavaScript" type="text/javascript" src="file:///C|/Users/CHarms/Documents/artisticcharms/index.php_files/rvscustomopenwindow.js"></script>

```

It should be like this:

```

<link rel="stylesheet" href="**style.css**" type="text/css">

```

In any type of development, it is nearly always best to adhere to the standards as much as possible. This reduces errors, improves compatibility, etc.

This will give you an idea of where the non-standard code is: [http://validator.w3.org/check?uri=http%3A%2F%2Fartisticcharms.com%2F&charset=(detect+automatically)&doctype=Inline&group=0&ss=1&outline=1&No200=1]("http://validator.w3.org/check?uri=http%3A%2F%2Fartisticcharms.com%2F&charset=(detect+automatically)&doctype=Inline&group=0&ss=1&outline=1&No200=1")

With the W3C standards, you don't need to fix all of it for everything to work OK in all the different browsers; you just want that number of errors to be much lower than it is now. One of the best ways of doing this is to use a standards compliant WYSIWYG editor/creator application. A decent WYSIWYG editor should also either automatically or by simple configuration set the relative path for you and not the local path.

You might want to try either [KompoZer]("http://kompozer.net/features.php") or [Amaya]("http://www.w3.org/Amaya/Amaya.html"), which I believe both are standards compliant.

---

### Post by radi0j0hn on 2009-05-08
Let me expand on "A lot of the content is local linked."

Sometimes a web editing program will put in the HTML that the file is located on the hard drive of the computer that is used to author the page.

Then, when the code is uploaded to the ISP, the code obviously can't find the file, as it is being told to look for it in a place that doesn't exist on the server.

Kompozer snags me on this often, probably due to me not clicking on something about "make files relative" to their location.  It's ALWAYS a good idea to look at the source code and try to find any references to "C:/ (anything)." That usually refers to your local drive.  This path can be erased and then the file is search for locally wherever it happens to be placed.

In some cases, you will not notice the errors, as the the files are on your hard drive, but someone else will not have them and they won't show up!

---


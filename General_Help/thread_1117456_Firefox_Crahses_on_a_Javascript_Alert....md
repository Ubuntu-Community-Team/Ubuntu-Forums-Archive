---
title: "Firefox Crahses on a Javascript Alert..."
date: 2009-04-06
forum: General Help
---

### Post by stndrdsnz on 2009-04-06
I've done some searching and I'm not finding much on this. This weekend I was without internet, and working on a website on my local machine. During a part of the website it pops up a Javascript Alert indicating if there is an error with the data submitted on the page, however, I noticed that sometimes when I would submit the form with bad data, Firefox would crash. After troubleshooting I narrowed it down to this javascript alert. To test things out I created a test html page that is shown below.

```

<html>
	<head><title>Alert Test</title></head>
	<body>
		<script>
			alert('Hello World');		
		</script>	
	</body>
</html>

```

This page will crash Firefox as well. Since I was offline this weekend I had no way to search further. However, I know that I had run some updates the day before. 

Here are some specs for my system:

Dell Vostro A860 laptop running Ubuntu 8.10

I noticed this problem start on April 4th, however, on the morning of April 3rd I ran the following updates:

Upgraded the following packages:
cups (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-bsd (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-client (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
cups-common (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
dpkg (1.14.20ubuntu6.1) to 1.14.20ubuntu6.2
dpkg-dev (1.14.20ubuntu6.1) to 1.14.20ubuntu6.2
firefox (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-3.0 (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-3.0-branding (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-3.0-gnome-support (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
firefox-gnome-support (3.0.7+nobinonly-0ubuntu0.8.10.1) to 3.0.8+nobinonly-0ubuntu0.8.10.2
gnome-user-guide (2.24.0+svn20080922ubuntu1) to 2.24.0+svn20080922ubuntu2
libcups2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
libcupsimage2 (1.3.9-2ubuntu7) to 1.3.9-2ubuntu8
libicu38 (3.8.1-2) to 3.8.1-2ubuntu0.1
libsndfile1 (1.0.17-4) to 1.0.17-4ubuntu0.8.10.1
libssl0.9.8 (0.9.8g-10.1ubuntu2.1) to 0.9.8g-10.1ubuntu2.2
libxine1 (1.1.15-0ubuntu3.1intrepid1) to 1.1.15-0ubuntu3.2
libxine1-bin (1.1.15-0ubuntu3.1intrepid1) to 1.1.15-0ubuntu3.2
libxine1-console (1.1.15-0ubuntu3.1intrepid1) to 1.1.15-0ubuntu3.2
libxine1-ffmpeg (1.1.15-0ubuntu3.1intrepid1) to 1.1.15-0ubuntu3.2
libxine1-gnome (1.1.15-0ubuntu3.1intrepid1) to 1.1.15-0ubuntu3.2
libxine1-misc-plugins (1.1.15-0ubuntu3.1intrepid1) to 1.1.15-0ubuntu3.2
libxine1-x (1.1.15-0ubuntu3.1intrepid1) to 1.1.15-0ubuntu3.2
openjdk-6-jre (6b12-0ubuntu6.1) to 6b12-0ubuntu6.4
openjdk-6-jre-headless (6b12-0ubuntu6.1) to 6b12-0ubuntu6.4
openjdk-6-jre-lib (6b12-0ubuntu6.1) to 6b12-0ubuntu6.4
openssl (0.9.8g-10.1ubuntu2.1) to 0.9.8g-10.1ubuntu2.2
xserver-common (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-core (2:1.5.2-2ubuntu3) to 2:1.5.2-2ubuntu3.1
xserver-xorg-video-intel (2:2.4.1-1ubuntu10.3) to 2:2.4.1-1ubuntu10.4
xulrunner-1.9 (1.9.0.7+nobinonly-0ubuntu0.8.10.1) to 1.9.0.8+nobinonly-0ubuntu0.8.10.1
xulrunner-1.9-gnome-support (1.9.0.7+nobinonly-0ubuntu0.8.10.1) to 1.9.0.8+nobinonly-0ubuntu0.8.10.1

I'm a strong believer in the statement that the most recent problem is directly related to the most recent change. Does anyone know if the Firefox upgrades that were run the day before may be causing this issue? Of Javascript code seems to be working ok, it's just the alert box that is failing.

If there is additional information I can provide for anyone to help me out, let me know I'd be glad to get it.

Thanks,

David

---

### Post by stndrdsnz on 2009-04-06
It's possible I may have jumped the gun in submitting this. I continued to have problems all weekend, even after shutting everything down, rebooting, etc. However, I came home, assuming I still had the problem and started searching for a resolution. After posting the problem I went to open up the test page I created and it worked. I disconnected from the internet and tried it again, and it worked, I changed Firefox from offline to online and it worked. So I'm not sure what the deal was. Anyone have any idea what may have been causing my problems? It was really frustrating as I was trying to debug an application and it would keep crashing on me. 

Thanks,

David

---


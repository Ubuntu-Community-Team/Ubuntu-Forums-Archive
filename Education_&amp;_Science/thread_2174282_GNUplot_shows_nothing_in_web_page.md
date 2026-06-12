---
title: "GNUplot shows nothing in web page"
date: 2013-09-13
forum: Education &amp; Science
---

### Post by GNUNewbie on 2013-09-13
Hi,

I am a newbie to GNUplot. I wrote a script that creates gnuplot graph and store that as html. When I run the script it creats the html page. It works well when I give the location of the html page in the browser "var/www/html/gnuplot.html". But when I call the same html page using the address, "localhost/gnuplot.html" I don't see the graph.  When I double click the html page I see the graph. Only when I use the address as "localhost/gnuplot.html", I don't see the graph. Could you please help me solve this issue?

---

### Post by tgalati4 on 2013-09-13
What are the permissions of the file?

```
ls -la /var/www/html/gnu*
```

It should be www-data:www-data, otherwise apache2 won't serve it.

Also, [http://localhost/html/gnuplot.html](http://localhost/html/gnuplot.html) might work.

If /var/www/html is indeed your root webserver directory, than you need to change the default in the apache configuration file.  /var/www is the default, not /var/www/html.

---

### Post by GNUNewbie on 2013-09-16
Thanks for your reply. I changed the user and group to apache as I am using apache server. My problem is I can open a gif file or other file format without any issues. Only when I try to open gnuplot file as html, I get this issue. When I save gnuplot as gif file and open it, it opens fine. Could you please tell me howto call a gnuplot html page from a php?

---

### Post by tgalati4 on 2013-09-16
Why don't you post what is in gnuplot.html? Perhaps it is a malformed file, so apache doesn't know what to do with it.

Not sure what your PHP code looks like, but have you gone through the PHP documentation for external program execution?  [http://php5.org/ref.exec.php](http://php5.org/ref.exec.php)

---

### Post by GNUNewbie on 2013-09-17
I wrote a script that creates GNUplot graph and saves it as gnuplot.html. Here is the script.


#!/bin/sh

echo "set term canvas mousing size 500, 500
set xlabel 'Feeder'
set ylabel 'Error count'
set object 1 rectangle from screen 0,0 to screen 1,1 fillcolor rgb'grey' behind
set output 'gnuplot.html' 
plot 'sample.txt' title 'Feeder-Error graph' with linespoints" | gnuplot

So gnuplot.html file just contains the graph.

---

### Post by SeijiSensei on 2013-09-17
If the file has an .html extension, browsers and the OS will assume it's written in HTML.  Why not save it as a graphic like .png?  [This posting]("http://stackoverflow.com/questions/9080832/output-png-from-gnuplot-is-not-as-good-as-the-figure-from-prompt-shell") has some help on getting good PNG results.  PDF might be a better choice, too.

There are some PHP interfaces to run GNUplot like [http://sourceforge.net/projects/php-gnuplot/](http://sourceforge.net/projects/php-gnuplot/).

---

### Post by tgalati4 on 2013-09-17
That was my point.  You need a properly-formatted html file with an html descriptor, headers, body, etc for a browser to view it.  The package that SeijiSensei suggests might do that.

---

### Post by GNUNewbie on 2013-09-17
Thanks for your response. I tried to save it as png and it works. With html format, I use canvas attribute and it looks more interactive than png. When I just double click to open gnuplot.html file as such, there is no problem. I can view it in the browser. Only when I use localhost to view the html file, I get this probelm.

---

### Post by tgalati4 on 2013-09-17
Look in /var/log/apache for apache errors as to why it won't open with localhost.  There may be a subtle permissions problem with localhost.  Try using the actual IP address instead and see if that works.  If that is the case, then you would need to put the server hostname in /etc/hosts.

---

### Post by GNUNewbie on 2013-09-18
Thanks for your response. I don't think there is permission porblem with localhost. I am able to open other html/php files in localhost without any problem. Only the file with gnuplot , I am not able to open.

---

### Post by GNUNewbie on 2013-09-19
Could anyone tell me how to use script file as img src in html? This is my code and I don't know how to make script file as img src.


<html>
<body>
<img src="test.sh" />
</body>
</html>

---

### Post by GNUNewbie on 2013-10-03
Could anyone please tell me how to output GNUPLOT canvas as html and use it in php page? all i see is blank pag without graph when i enter the url in the browser

---

### Post by tgalati4 on 2013-10-03
Image source has to refer to a specific image file not a script.  You need a way to trigger running the script to generate the image file "mygnuplot.png" then put the full path and filename in the image source universal resource locator.

I have found going through some of these tutorials helpful:  [http://www.w3schools.com/html/](http://www.w3schools.com/html/)

---

### Post by GNUNewbie on 2013-10-04
Thanks for your response. I am able to create a image file from script. I want to create a image file with html extension using gnuplot canvas. With this I can see co-ordinates in the graph. It shows x and y co-ordianates. With png I don't see that. I created ascript to save the output as html. it works fine whtn I just open the html file. But when I try to access the html file from the php file in a webpage, I get blank graph.

This is my script to generate gnupot graph as html file.

echo "set term canvas mousing size 500, 500
set xlabel 'Feeder'
set ylabel 'Error count'
set object 1 rectangle from screen 0,0 to screen 1,1 fillcolor rgb'grey' behind
set output 'gnuplot.html' 
plot 'sample.txt' title 'Feeder-Error graph' with linespoints" | gnuplot

---

### Post by GNUNewbie on 2013-10-04
Thanks for your response. I am able to create a image file from script. I want to create a image file with html extension using gnuplot canvas. With this I can see co-ordinates in the graph. It shows x and y co-ordianates. With png I don't see that. I created ascript to save the output as html. it works fine whtn I just open the html file. But when I try to access the html file from the php file in a webpage, I get blank graph.

This is my script to generate gnupot graph as html file.

echo "set term canvas mousing size 500, 500
set xlabel 'Feeder'
set ylabel 'Error count'
set object 1 rectangle from screen 0,0 to screen 1,1 fillcolor rgb'grey' behind
set output 'gnuplot.html' 
plot 'sample.txt' title 'Feeder-Error graph' with linespoints" | gnuplot

---


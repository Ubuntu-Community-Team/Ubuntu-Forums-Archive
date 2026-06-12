---
title: "weather station"
date: 2014-04-17
forum: Education &amp; Science
---

### Post by Peter1981 on 2014-04-17
Hi

I would like to make a server. I already installed Ubuntu 12.04 LTS. No graphics screen.
I would install Apache to share website. And here starts my problem.
My plan is to buy a weather station like this: [http://www.ebay.co.uk/itm/Black-Wireless-Pro-Weather-Station-Touch-LCD-Screen-with-PC-USB-Interface-/151280890898?pt=UK_BOI_Electrical_Test_Measurement_Equipment_ET&hash=item23390b3412](http://www.ebay.co.uk/itm/Black-Wireless-Pro-Weather-Station-Touch-LCD-Screen-with-PC-USB-Interface-/151280890898?pt=UK_BOI_Electrical_Test_Measurement_Equipment_ET&hash=item23390b3412)
Is there a program to get the data from the device and upload to the server?
Or if it is not compatible to any Linux weather software could you recommend another one?
I do not have too much programming experience.
What I need: Get the data from the device and convert it to HTML file. It would be enough for me. But if there is a program to convert the data with diagram and signs to a JPG file that would be really good.
I can make the website (not a professional one, but would be enough) and add the file but I do not know how to get the latest file. So I would need a program to get the latest file from the directory and change it in the html file.

Can someone help me to have this project done.

Thanks

Ps. Sorry for my plain english

---

### Post by tgalati4 on 2014-04-17
That is a nice system for the price.  Most of these weather stations transmit a large data packet that can be parsed to extract the weather details.  Then you can use gnuplot or perhaps html5 charting commands to display your data on your server.  You will have to continue your search for that particular model to see if someone has written a script to grab the data.

I have an old weather station that my neighbor gave to me that had a serial port.  I found a script that someone wrote to parse the data.   So I would keep searching.  Check the Weather Underground forums for recommended station kits.  The good ones are kind of expensive.

---


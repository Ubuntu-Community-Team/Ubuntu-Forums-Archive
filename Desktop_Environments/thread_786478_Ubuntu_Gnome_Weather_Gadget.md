---
title: "Ubuntu Gnome Weather Gadget"
date: 2008-05-08
forum: Desktop Environments
---

### Post by ponx on 2008-05-08
Hi, just a curiosity, but when using the weather gadget on the gnome panel, the choices of location are somewhat obscure..!?

Is it possible to get locations other than those provided..?  It doesn't have major towns like Portsmouth (UK) or Brighton, the nearest I can get is Southampton...

(The weather gadget for Xfce panel DOES have these choices)

Cheers.

ponx

---

### Post by Kevbert on 2008-05-08
A way round this is to get the ClearWeather screenlet which downloads data from Weather.com It has data for both Portsmouth and Brighton.
Screenlets can be downloaded here: [http://screenlets.org/index.php/Download]("http://screenlets.org/index.php/Download")

Weather.com recently updated their website so you'll need to edit some code.
Open terminal and enter 
sudo gedit /usr/share/screenlets/ClearWeather/ClearWeatherScreenlet.py

Look for two lines with 'http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&par=1...
and enter  
[COLOR="Red"]&link=xoap[/COLOR] in each line so it now reads
'http://xoap.weather.com/weather/local/'+self.ZIP+'?cc=*&dayf=10&prod=xoap&link=xoap&par=1...

Save the file once both lines are edited and then exit terminal

Next run the ClearWeather screenlet by opening Screenlets and clicking on the ClearWeather icon.

Right-click on the ClearWeather box (screenlet) that is displayed and select Zip Code.

Next open a browser and enter weather.com
next enter the place you require (eg Brighton)
Select the UK one and press return
In the address bar the following is displayed
[www.weather.com/outlook/travel/businesstraveler/local/UKXX0215?from=search_city](www.weather.com/outlook/travel/businesstraveler/local/UKXX0215?from=search_city)
(Displays local/UKXX0215?from=search_city)
So in the case of Brighton you would enter UKXX0215 as your zip code.

Hope this is of use.

---

### Post by ponx on 2008-05-08
Cheers Kevbert, I will try this out later on...

ponx

---


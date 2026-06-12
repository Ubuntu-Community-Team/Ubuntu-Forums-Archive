---
title: "Conky Weather Python Script"
date: 2008-04-20
forum: Desktop Effects &amp; Customization
---

### Post by kaivalagi on 2008-04-20
[COLOR="Blue"][SIZE="5"]**IMPORTANT**[/SIZE][/COLOR]
If you have any questions you'll need to post them on the newer thread here: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
Also newer additions to the script can't be found here, in fact I have removed the script download...so you'll need to head to the new thread anyways
This thread has been outdated, it's been in and out of the archive...and I do not wish to update 2 threads everytime







[COLOR="Blue"]_**[SIZE="4"]Intro[/SIZE]**_[/COLOR]

This post follows on from my previous one [here]("http://ubuntuforums.org/showthread.php?p=4752214")

I have recently put together a python script to produce various bits of weather data on demand for use in Conky. This sort of thing has been done already by lvleph, a post for his contribution is [here]("http://ubuntuforums.org/showthread.php?t=666842"). 

I wanted to create something, firstly to gain some experience with Python, and secondly so that there was no dependency on the yahoo weather website and it's formatting. This hopefully means that it will have a little longevity.

Some key features
[LIST]
[*]Utilises the weather.com XOAP service.
[*]Caches fetched data to stop unnecessary web calls
[*]Supports ranged forecast output, up to the next 5 days (cut's down on execi calls :) )
[*]Optional spacing settings for ranged input
[*]Supports imperial / metric measurements
[*]Supports day or night forecasts
[*]Provides limited language support (english default, optional spanish, more if help provided)
[*]Supports template files for complicated output in a single exec call! (cut's down on execi calls big time :) )
[/LIST]

Hope some of you find it useful

Any suggestions, please speak up. 



[COLOR="Blue"]_**[SIZE="4"]Steps To Get It Working[/SIZE]**_[/COLOR]

[COLOR="Blue"]**[SIZE="3"]Step 1: Dependencies[/SIZE]**[/COLOR]

Ensure you have the package dependencies, currently only python:

```
sudo apt-get install python
```

[COLOR="Blue"]**[SIZE="3"]Step 2: Install the weather, arrows and moon phase fonts[/SIZE]**[/COLOR]

Extract the ttf's, from the attached Fonts.tar.gz file, to your desktop. Once there run the following (copy and register). Note: if you don't have a .fonts folder create one using "mkdir ~/.fonts" first.

```
cp ~/Desktop/*.ttf ~/.fonts/ && fc-cache -f -v
```

[COLOR="Blue"]**[SIZE="3"]Step 3: Install the script[/SIZE]**[/COLOR]

Extract the python script called conkyForecast.py, from the attached conkyForecast.tar.gz file, to ~/.scripts/conkyForecast.py for example, and make sure it is executable like so:

```
chmod a+x ~/.scripts/conkyForecast.py
```


[COLOR="Blue"]**[SIZE="3"]Step 4: Weather.com XOAP Service Registration[/SIZE]**[/COLOR]

Due to the risk of having the previously registered xoap weather.com account terminated because of high volumes of requests, I have upgraded the script to use a users own registered details. 

The following are the lines in the script, which will require your own registration codes (Partner ID & License Key):

```
XOAP_PAR = u"1234567890" #Invalid code, needs replacing
XOAP_KEY = u"ac12ab12ab12ab12" #Invalid code, needs replacing
```

To register and obtain the necessary codes you need to visit [http://www.weather.com/services/xmloap.html]("http://www.weather.com/services/xmloap.html") and fill out the required form. 

After successfully completing the form, you will then receive a couple of emails providing you with the necessary codes to update conkyForecast with, along with the software development kit and terms and conditions.


[COLOR="Blue"]**[SIZE="3"]Step 5: Location Code For Script Calls[/SIZE]**[/COLOR]

To identify the location code for your town/city the following URL should be used, replacing NORWICH with the one you're looking up :

[http://xoap.weather.com/search/search?where=NORWICH]("http://xoap.weather.com/search/search?where=NORWICH")

The following xml is returned for the above url, from which the correct location code (loc id value) can be picked. Mine was UKXX0103.
```
<search ver="2.0">
  <loc id="USNY0428" type="1">East Norwich, NY</loc>
  <loc id="USNY1036" type="1">North Norwich, NY</loc>
  <loc id="USCT0155" type="1">Norwich, CT</loc>
  <loc id="UKXX0103" type="1">Norwich, United Kingdom</loc>
  <loc id="USKS0428" type="1">Norwich, KS</loc>
  <loc id="USND0266" type="1">Norwich, ND</loc>
  <loc id="USNY1044" type="1">Norwich, NY</loc>
  <loc id="USOH0716" type="1">Norwich, OH</loc>
  <loc id="USVT0175" type="1">Norwich, VT</loc>
</search>
```

Once you know your location code, use it when calling the script with the "*--location=*" option.

[COLOR="Blue"]**[SIZE="3"]Step 6: Testing[/SIZE]**[/COLOR]

Extract the conkyrc-test, conkyrc-test-template and conkyForecast.template files, from the attached conkyForecast.tar.gz, to your desktop. To test conky run the following:

```
conky -c ~/Desktop/conkyrc-test
```

To test conky using templates run this:

```
conky -c ~/Desktop/conkyrc-test-template
```

Bear in mind that the --template option used in the above file must not be the short form path to your template file using the ~ symbol. Unfortunately conky will not translate the ~ symbol in relation to your home directory. You will HAVE to modify the conkyrc-test-template file to point to the full path to your .template file.


[COLOR="Blue"]_**[SIZE="4"]Usage Help[/SIZE]**_[/COLOR]

You can get the current help options at any time by running (change the path as necessary):

```
python ~/.scripts/conkyForecast.py -h
```

or

```
python ~/.scripts/conkyForecast.py --help
```

The usage is as follows:

```
Usage: conkyForecast.py [options]
Options:
  -h, --help            show this help message and exit
  -lCODE, --location=CODE
                        location code for weather data [default: UKXX0103],Use
                        the following url to determine your location code by
                        city name:
                        http://xoap.weather.com/search/search?where=Norwich
  -dDATATYPE, --datatype=DATATYPE
                        [default: HT] The data type options are: DW (Day Of
                        Week), WF (Weather Font Output), LT (Forecast:Low
                        Temp,Current:Feels Like Temp), HT (Forecast:High
                        Temp,Current:Current Temp), CC (Current Conditions),
                        CT (Conditions Text), PC (Precipitation Chance), HM
                        (Humidity), WD (Wind Direction), WS (Wind Speed), WG
                        (Wind Gusts), CN (City Name), SR (sunrise), SS
                        (sunset), MP (moon phase), MF (moon font), BR
                        (barometer reading), BD (barometer description), UI
                        (UV index), UT (UV text), DP (dew point). Not
                        applicable at command line when using templates.
  -sNUMBER, --startday=NUMBER
                        define the starting day number, if omitted current
                        conditions are output. Not applicable at command line
                        when using templates.
  -eNUMBER, --endday=NUMBER
                        define the ending day number, if omitted only starting
                        day data is output. Not applicable at command line
                        when using templates.
  -SNUMBER, --spaces=NUMBER
                        [default: 1] Define the number of spaces between
                        ranged output. Not applicable at command line when
                        using templates.
  -tFILE, --template=FILE
                        define a template file to generate output in one call.
                        A displayable item in the file is in the form
                        {--datatype=HT --startday=1}. The following are
                        possible options within each item: --datatype,--
                        startday,--endday,--night,--shortweekday,--imperial,--
                        hideunits,--spaces . Note that the short forms of the
                        options are not currently supported! None of these
                        options are applicable at command line when using
                        templates.
  -LLOCALE, --locale=LOCALE
                        override the system locale for language output
                        (en=english, es=spanish, fr=french, more to come)
  -i, --imperial        request imperial units, if omitted output is in
                        metric. Not applicable at command line when using
                        templates.
  -n, --night           switch output to night data, if omitted day output
                        will be output. Not applicable at command line when
                        using templates.
  -w, --shortweekday    Shorten the day of week data type to 3 characters. Not
                        applicable at command line when using templates.
  -u, --hideunits       Hide units such as mph or C, degree symbols (°) are
                        still shown. Not applicable at command line when using
                        templates.
  -v, --verbose         request verbose output, no a good idea when running
                        through conky!
  -r, --refetch         fetch data regardless of data expiry
```

**Note:** For current conditions the temperature is the same when either the HT or LT datatype is used.

[COLOR="Blue"]_**[SIZE="4"]Notes On Conky Config Files[/SIZE]**_[/COLOR]

I recommend using the test files as a templates when creating your own conkyrc file. Note that if the location of the python script is different to the example given, please ensure the conkyrc-test* file, or your own, is amended to point to the correct location.

A quick example of use in conky config:

```
Conditions: ${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX0103 --datatype=CC}
${font Weather:size=36}${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX0103 --datatype=WF}${font}
Temp: ${execi 3600 python ~/.scripts/conkyForecast.py --location=UKXX0103 --datatype=HT}
```

More conky documentation can be found on the conky sourceforge site, quick links below:
[LIST]
[*] [~.conkyrc settings]("http://conky.sourceforge.net/config_settings.html")
[*] [Conky Variables]("http://conky.sourceforge.net/variables.html")
[*] [Conky Manual]("http://conky.sourceforge.net/docs.html")
[/LIST]

[COLOR="Blue"]_**[SIZE="4"]Notes On Template Files[/SIZE]**_[/COLOR]

Recently the use of templates was added, so that a single exec call can be made to retrieve a multitude of data. 

An example template file is included in the attached conkyForecast.tar.gz, and the usage text also explains the options available.

Note that you will not be able to combine standard font output with weather fonts in a single template. Font configuration is done inside the conkyrc file and so makes this impossible. A separate weather font based output can be generated and offsets can be used in the conkyrc to line up the data properly. Many of the "thread posters" can help in your offset endeavours I am sure. 

A quick example of template file options and layout:

```
   {--datatype=DW --startday=1 --shortweekday}

{--datatype=HT --startday=1 --hideunits}/{--datatype=LT --startday=1 --hideunits}
```

Anything inside the curly brackets are options, outside of the brackets is standard text that will be output "as is".

[COLOR="Blue"]_**[SIZE="4"]Notes On Script Config Values[/SIZE]**_[/COLOR]

The conkyForecast.py script has a few config values worthy of a mention.

[COLOR="Blue"]**Cached data file locations**[/COLOR]

The following are the default file locations for any fetched and prepared data from the weather.com. You can change these if you so wish, but please make sure the LOCATION text remains in the name as this is replaced with your location code on their creation.

```
TEMP_FILEPATH_CURRENT = "/tmp/conkyForecast-c-LOCATION.pkl"
TEMP_FILEPATH_DAYFORECAST = "/tmp/conkyForecast-df-LOCATION.pkl"
TEMP_FILEPATH_NIGHTFORECAST = "/tmp/conkyForecast-nf-LOCATION.pkl"
```

[COLOR="Blue"]**Expiry Setting**[/COLOR]

The following is the default expiry setting in the current script. It defines when new data should be retrieved from weather.com or not, when the script is executed, based on how old the current data held is.

```
EXPIRY_MINUTES = 30
```

Feel free to search and change the value if you need to.

[COLOR="Blue"]_**[SIZE="4"]Gotchas[/SIZE]**_[/COLOR]

1) Conky has a default limitation of 128 bytes for any text output from a variable (such as execi). If you are creating large templates with more characters than the default buffer size can handle, the output will get truncated. If this happens you can override the default behaviour by setting as new buffer size at the top of your conkyrc file, as follows:
```
text_buffer_size 256
```

2) There is a limit to the maximum range for forecasts, the startday and endday options cannot be set greater than 4, otherwise the script breaks...the following are the options to use to get the maximum forecast of high temps (including forecast data for today):
```
--datatype=HT --startday=0 --endday=4
```

[COLOR="Blue"]_**[SIZE="4"]Development History[/SIZE]**_[/COLOR]

Created: 13/04/2008
Modifications:
[LIST]
[*]14/04/2008	Allow day ranges for forecast data
[*]14/04/2008	Check for connectivity to xoap service
[*]18/04/2008	Allow the setting of spaces for ranged output
[*]18/04/2008	Allow Night and Day forecast output
[*]18/04/2008	Support locale for condition code text "CC" option, awaiting spanish language translation
[*]18/04/2008	Use pickling for class data rather than opening xml, this bypasses the need to interrogate cached data
[*]19/04/2008	Added spanish condition text - Thanks Bruce M
[*]19/04/2008	Added isnumeric check on all numeric output with units suffix
[*]19/04/2008	Altered pickle file naming to include location code
[*]19/04/2008	Added spanish week days conversion via locale
[*]20/04/2008	Added decent command argument parser
[COLOR="Blue"]
[*]20/04/2008	Added --shortweekday option, if given the day of week data type is shortened to 3 characters
[*]21/04/2008	Fixed locale options for forecast output
[*]21/04/2008	Added --template option to allow custom output using a single exec call :)
[*]21/04/2008	Added --hideunits option to remove, for example, mph and C from output
[*]23/04/2008	Removed --imperial option from template, this MUST be set as a standard option on the script call  and not used in the template file.
[*]23/04/2008	Readded --imperial option to template, enabling metric or imperial values per datatype. Note when using templates command line option will not work.
[*]23/04/2008	Added output notifying user if the location given is bad
[*]24/04/2008	Added handling for no connectivity, will revert to cached data now (erroring if no cache exists). Tests by trying to open xoap.weather.com
[*]24/04/2008	Fixed Celsius to Fahrenheit conversion
[*]06/05/2008	Updated url used for weather data due to webservice update
[*]09/05/2008	Consolidated current condition and forecast data fetch into one call
[*]09/05/2008	Added Sunrise and sunset to datatypes, these are specific to both current conditions and forecast data
[*]09/05/2008	Added moon phase, barometer reading and barometer description to datatypes, these are only specific to current conditions and so are N/A in forecast output
[*]09/05/2008	Added unit conversions for barometer from mb to inches (imperial)
[*]09/05/2008   Updated Spanish condition text - Thanks Bruce M
[*]10/05/2008  Added french locale data - Thanks benpaka
[*]12/05/2008  Added new BF (bearing font) datatype to provide an arrow character (use with Arrow.ttf font) as an alternative to the NSEW output from WD (wind direction)
[*]12/05/2008  Updated WD output to be locale specific, currently supports default english, spanish and french - Thanks Bruce M / jjgomera
[*]18/05/2008	Added new MF (moon font) datatype to provide a moon font character (characters incorrect and no dedicated font yet).
[*]21/05/2008	For current conditions the --datatype=LT option now displays "feels like" temperature rather than the current temperature
[*]28/05/2008	Arrows reported to be pointing in the wrong direction. Correction provided by jjgomera
[*]03/06/2008	Updated MF function, added days #26, #27, #28 and #29 to complete the cycle. Corrections provided by Bruce M/uboops/HippyRandall
[*]15/06/2008	Added new UI (UV index), UT (UV text), DP (dew point) datatypes
[*]18/06/2008	Updated DP (dew point) output to convert to imperial units when required - thanks HippyRandall
[*]18/06/2008	Added Spanish and French translations for UV text - Thanks Bruce M.
[*]18/06/2008	Fixed incorrect WSW bearing text translation for Spanish and French - thanks Bruce M. 
[*]18/06/2008	Updated to now use users own registration details from weather.com, visit [http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html) to register and obtain the PAR and KEY codes
[*]06/07/2008	Added check for invalid licence key error in returned xml and now display "*** ERROR: Invalid License Key ***" in output if found...
[/COLOR]
[/LIST]
[COLOR="Blue"]Blue[/COLOR] modifications have been added since posting this thread.

Bear in mind there may be features you are missing out on if you haven't downloaded the script recently. Also note I have tried to ensure that any script modifications do not cause existing conky configurations to break, so updating the script shouldn't cause any issues. This was the main reason for switching to use a decent command argument parser.

---

### Post by TB2 on 2008-04-20
Thanks for your work!
Gonna try it out right away...

edit: Working here :)
btw, that error I got earlier was just me having mistyped the area code. SZXX003 should have been SZXX0003. Skipped a 0 there...

---

edit: There's a problem when using your script with the $alignc option in conky. Looking at this example:
```
${voffset 10}${color}3 day forecast
${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=1 --datatype=DW}[COLOR="Red"]${alignc}[/COLOR]${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}[COLOR="Red"]${alignr}[/COLOR]${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=3 --datatype=DW}	
${alignc}asdf
```
displays like this:

[img]http://img440.imageshack.us/img440/990/notcenteredcp3.png[/img]

so the weekday in the middle won't be centered. The "asdf" below shows where "Tuesday" should be standing.

Do you have any idea how to make this work? Because using offsets or just blankspaces between the script calls i no option as the lenght of the day names is variable so it would be different for each day.

---

### Post by kaivalagi on 2008-04-20
> **TB2 said:**
> 
edit: There's a problem when using your script with the $alignc option in conky. Looking at this example:
```
${voffset 10}${color}3 day forecast
${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=1 --datatype=DW}[COLOR="Red"]${alignc}[/COLOR]${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}[COLOR="Red"]${alignr}[/COLOR]${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=3 --datatype=DW}	
${alignc}asdf
```
...
so the weekday in the middle won't be centered. The "asdf" below shows where "Tuesday" should be standing.

Bizarre! I've checked the output, and there are no extra spaces around the weekday text.  I also put a single call underneath the 3 week days, to see whether it lined up with the adsf and it more of less does. I think this might be an issue with the align functions in conky...

e.g.

```
${voffset 10}${color}3 day forecast
${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=1 --datatype=DW}${alignc}${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}${alignr}${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=3 --datatype=DW}
${alignc}${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}	
${alignc}asdf
```

Did you use a different script before now and not have this problem? Maybe I can reproduce what has been done already with another script?

I'll give it some more thought

[COLOR="Blue"]**Bruce M** - have you come across this conky align problem and it's solution?[/COLOR]

---

### Post by Bruce M. on 2008-04-20
> **TB2 said:**
> There's a problem when using your script with the $alignc option in conky. Looking at this example:
```
${voffset 10}${color}3 day forecast
${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=1 --datatype=DW}[COLOR="Red"]${alignc}[/COLOR]${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}[COLOR="Red"]${alignr}[/COLOR]${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=3 --datatype=DW}	
${alignc}asdf
```
displays like this:

[img]http://img440.imageshack.us/img440/990/notcenteredcp3.png[/img]

so the weekday in the middle won't be centered. The "asdf" below shows where "Tuesday" should be standing.

Do you have any idea how to make this work? Because using offsets or just blankspaces between the script calls i no option as the lenght of the day names is variable so it would be different for each day.

> **kaivalagi said:**
> Bizarre! I've checked the output, and there are no extra spaces around the weekday text.  I also put a single call underneath the 3 week days, to see whether it lined up with the adsf and it more of less does. I think this might be an issue with the align functions in conky...

e.g.

```
${voffset 10}${color}3 day forecast
${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=1 --datatype=DW}${alignc}${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}${alignr}${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=3 --datatype=DW}
${alignc}${execi 3600 python /pathto/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}	
${alignc}asdf
```

Did you use a different script before now and not have this problem? Maybe I can reproduce what has been done already with another script?

I'll give it some more thought

[COLOR="Blue"]**Bruce M** - have you come across this conky align problem and it's solution?[/COLOR]

Yes, it's not that hard but one must remember a few things:

[LIST=1]
[*] using  a mono font is "critical" with weather, in my opinion, spacing
[*] shorten displayed day names to: Mon Tue, Wed, Thu, Fri Sat Sun
[/LIST]

When you have:```
Monday   Tuesday   Wednesday
```even in mono fonts Monday = 6 characters, Tuesday = 7 and Wednesday =9

Lets take an example of a conky that is "200" wide.
Monday and Wednesday take up 15 character spaces and Tuesday needs 7. The conky {alignc} will put the "s" in Tuesday in the "center of the unused area IE: 185. therefore "s" would go in at 92.5. not 100.

Now if it was```
Mon   Tue   Wed
```that would leave 194 spaces and the "u" would be centered in at 87 of the remaining spaces. which in theory should be 100 on an empty line.

Now here is where we run into another problem. When we use {alignc} we can move things left with a positive number ie: {alignc 2} and move things to the right of center with a negative number {alignc -2}. The problem is that this command is in pixels not character spacing and the weather.ttf font is NOT a mono font. So aligning things is at best a touch and go thing.

Now another factor comes into play the {offset} command ... since most people want something like:```
Mon   Tue   Wed
WF   WF   WF
stuff   stuff   stuff
```{offset} becomes critical. for example:

```
${command to display 3 day names}
${command to display 3 days of weather fonts}
${hi/low command}
```

might result in:
```
MonTueWed
**          ***          ****
27°C/19°C29°C/17°C32°C/22°C
```

Notice the (**  ) representing "the sun" for clear skies, (*** ) for cloudy and (****) for thunderstorms (and that is roughly how they are regarding the size of the displays. What you "see" on the output is only the ** part.

The "first thing to do is {alignc} the weather font and then adjust it so it is "relatively" in the center..  It would be perfect if you have three days of thunderstorms showing.  You'll most likely be addin negative numbers to the {alignc} command.
ie:
```
${command to display 3 day names}
${alignc -15}${command to display 3 days of weather fonts}
${hi/low command}
```

might result in:
```
MonTueWed
              **          ***          ****
27°C/19°C29°C/17°C32°C/22°C
```
Next us the {offset} command for the 3 day names to get Mon above the proper weather font:
```
${offset -26}${command to display 3 day names}
${alignc -15}${command to display 3 days of weather fonts}
${hi/low command}
```

might result in:
```
             MonTueWed
              **          ***          ****
27°C/19°C29°C/17°C32°C/22°C
```
Now start playing with the "spacing" between the day names" and adjust the {offset xx} to keep Mon aligned over the proper symbol.

Repeat the process for the Hi/Lows

**In my opinion:**
[LIST=1]
[*] If the **.PY** file could be programmed to use "pixels" versus "character spacing" things could come much more into line. 
[*] Or ideally "2 pixel spacing commands" one for "before" day names and one for "after" day names.  I realize that's asking a lot of kaivalagi and it may not even be possible in a **PY** script. I don't know I'm not a programmer.
[*] While pixel spacing was never implemented in the **.PL** file, it was being looked at to see if it was possible. It did, however, have "character spaces" before and after day names.
[/LIST]

**So commands to use in conky:**
Center: {alignc}
Move Right: {alignc -x}
Move Left: {alignc x}

Move Right: {offset -x}
Move Left: {offset x}

Move Up: {voffset -x}
Move Down: {voffset x}

Right: {alignr}
Right and move 2 pixels left from the boarder {alignr 2}

Combine them: ${alignc 10}${voffset -42} puts info beside the weather font symbol like I use: ```
${alignc 10}${voffset -42}Max: ${execi 3600 python ~/scripts/conkyForecast.py ARBA0009 M HT 2}
```

Does that help?

Have a great day.
Bruce

---

### Post by TB2 on 2008-04-20
It could just as well be my .conkyrc as it's badly written and hacked to death. ;) I think my borders aren't defined the right way. Anyways, here is what I've done now.

```
${voffset 10}${color}3 day forecast
${voffset 6}${color #B3B3B3}${offset 15}${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 --startday=1 --datatype=DW}${alignc}${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=DW}
${voffset -16}${alignr}${offset 8}${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 --startday=3 --datatype=DW}	
${font weather:size=33}${offset 20}${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 --startday=1 --datatype=WF}
${voffset -58}${offset 200}${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=WF}
${alignr}${voffset -57}${offset -60}${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 --startday=2 --datatype=WF}$font
${offset 7}${execi 3600 python /path/to/conkyForecast.py --startday=1 --location=SZXX0014 --datatype=HT}/${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 -n --startday=1 --datatype=HT}${alignc}${execi 3600 python /path/to/conkyForecast.py --startday=2 --location=SZXX0014 --datatype=HT}/${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 -n --startday=2 --datatype=HT}
${voffset -16}${alignr}${execi 3600 python /path/to/conkyForecast.py --startday=3 --location=SZXX0014 --datatype=HT}/${execi 3600 python /path/to/conkyForecast.py --location=SZXX0014 -n --startday=3 --datatype=HT}

[COLOR="Red"]asdf${alignc}asdf${alignr}asdf[/COLOR]
```

It looks like this:

[img]http://img440.imageshack.us/img440/7063/notcentered1wp7.png[/img]

So as you can see, even if I just use "asdf" for those three alignments (I highlighted them at the end of the code above) the middle "asdf" isn't really centered. It seems like putting the third entry (with ${alignr}) on a new line and us ${voffset} solves the problem. But that's just another dirty hack. It doesn't really look right atm. I wished conky would support columns so that it'd be possible to define 3 rows with centered content for thins like this. But that's another story ;)

Btw, my whole .conkyrc is [_here_](http://rafb.net/p/45kIXx24.html).
And here's a screenshot of it:

[[img]http://img440.imageshack.us/img440/9440/conkynotcentered2or5.th.png[/img]](http://img440.imageshack.us/img440/9440/conkynotcentered2or5.png)

(click to enlarge)


> shorthen displayed day names to: Mon Tue, Wed, Thu, Fri Sat SunThat's a very smart idea. Would be nice if the weatherscript would provide that option.

---

### Post by kaivalagi on 2008-04-20
> **TB2 said:**
>  Would be nice if the weatherscript would provide that option.

Just added a --shortweekdays option :) See the top post for details and download

Also works in Spanish, Bruce you may want to check the weekday abbreviations though?

[COLOR="Navy"]Edit:[/COLOR]
> **TB2 said:**
> I wished conky would support columns so that it'd be possible to define 3 rows with centered content for thins like this. But that's another story
I asked a similar question about formatting in the #conky irc channel on freenode. I wondered if we could have html formatting added into conky, so tables could align things nicely, images would be supported for weather forecasting and css style sheets would be usable for switching look and feel easily. There is nothing in the pipelines as far as I'm aware :(
Maybe someone should write a new conky with this support???

---

### Post by dccrens on 2008-04-20
> **kaivalagi said:**
> 

**Step 3:** Extract the attached script called conkyForecast.py as ~/.scripts/conkyForecast.py for example, and make sure is executable:



kaivalagi,
Thanks! Figured out my questions...

Edit: Scratch that. .. The py is not in the zip file. Only the weather font is...

---

### Post by kaivalagi on 2008-04-20
> **dccrens said:**
> kaivalagi,
Thanks! Figured out my questions...

Edit: Scratch that. .. The py is not in the zip file. Only the weather font is...

The conkyForecast.tar.gz has everything except the weather font in it

If the instructions aren't clear, let me what needs more detail etc  [COLOR="Navy"]Edit: added more detail, does it read better?[/COLOR]

---

### Post by Bruce M. on 2008-04-20
> **kaivalagi said:**
> Just added a --shortweekdays option :) See the top post for details and download

Also works in Spanish, Bruce you may want to check the weekday abbreviations though?

Just checked them, they are what I use.  :) Don't have a clue if it is "official" or not but for ascetic reasons that is what I use.

You're fast  :)

Quick question.
If I download and over write my PY file with the latest PY file, is it backwards compatible with older versions regarding info, spacing commands and such?

Have a great day
Bruce

---

### Post by kaivalagi on 2008-04-20
> **Bruce M. said:**
> 
Quick question.
If I download and over write my PY file with the latest PY file, is it backwards compatible with older versions regarding info, spacing commands and such?
Bruce

If you are running a conkyrc for a  py from the previous thread then it will break. You'll need to place prefixes on the arguments and possibly re-arrange some (--night now instead of a D or N for example)

If you download the script on this thread and get it working, you shouldn't need to update your conkyrc if you replace the py afterwards.

I have totally changed the way arguments are passed to the script so that it is compatible like this going forwards.

Cheers

P.S. The script is easily modifiable, hence the speediness of the enhancements. I wish it was this simple at work :)

---

### Post by Bruce M. on 2008-04-20
> **kaivalagi said:**
> If you are running a conkyrc for a  py from the previous thread then it will break. You'll need to place prefixes on the arguments and possibly re-arrange some (--night now instead of a D or N for example)

If you download the script on this thread and get it working, you shouldn't need to update your conkyrc if you replace the py afterwards.

I have totally changed the way arguments are passed to the script so that it is compatible like this going forwards.

Cheers

Perfect ... OK, I'll play.  :)
Thanks
Bruce

---

### Post by mojohn on 2008-04-20
Kaivalagi, I just downloaded your most recent conkyrc and conkyForecast.py from this thread. I have a question: what goes in this line of the Forecast script?


	 			url = 'http://xoap.weather.com/weather/local/' + self.options.location + '?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39'

To get the weather for my city, this is the url:

[http://www.weather.com/weather/local/64068?lswe=64068&lwsa=WeatherLocalUndeclared&from=whatwhere](http://www.weather.com/weather/local/64068?lswe=64068&lwsa=WeatherLocalUndeclared&from=whatwhere)

Thanks,

mojohn

---

### Post by kaivalagi on 2008-04-20
> **mojohn said:**
> Kaivalagi, I just downloaded your most recent conkyrc and conkyForecast.py from this thread. I have a question: what goes in this line of the Forecast script?


	 			url = 'http://xoap.weather.com/weather/local/' + self.options.location + '?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39'

To get the weather for my city, this is the url:

[http://www.weather.com/weather/local/64068?lswe=64068&lwsa=WeatherLocalUndeclared&from=whatwhere](http://www.weather.com/weather/local/64068?lswe=64068&lwsa=WeatherLocalUndeclared&from=whatwhere)

Thanks,

mojohn

As mentioned in the usage text, use the url below with a where=? to suit your location e.g.

[http://xoap.weather.com/search/search?where=liberty]("http://xoap.weather.com/search/search?where=liberty")

Based on this, the location code for Liberty, MO is USMO0519.

The code used for this is not the same as the standard weather.com website, because is relates to an xml service instead (xoap). Funnily enough the location code used in standard Yahoo Weather url's is the same as the xoap service one...

I'm going to update the guide above for this[COLOR="Blue"] - Updated[/COLOR]

Cheers

---

### Post by Bruce M. on 2008-04-20
With regard to my post [#4]("http://ubuntuforums.org/showpost.php?p=4753259&postcount=4") where I mention:

> Notice the (** ) representing "the sun" for clear skies, (*** ) for cloudy and (****) for thunderstorms (and that is roughly how they are regarding the size of the displays. What you "see" on the output is only the ** part.

The attached image is a perfect example.
The two sunny symbols under the red arrow line up, because there are the same symbols before it, even though in different order.

But starting at the yellow line things start to get a little misplaced so formatting your spacing over/under the weather fonts can be tricky. at best.

Mono fonts really help here
Have fun.
Bruce

---

### Post by yousillygoose on 2008-04-20
a quick note: i didn't see anyone say this but if they did i appologize for repeating.  I think having a function for HT/LT would be useful.  I am using your startday and endday definitions.  I cannot do this for HT and LT if I want to have it in the HT/LT format because the output would be:

HT HT HT HT HT / LT LT LT LT LT

Any thoughts?

---

### Post by yousillygoose on 2008-04-20
Well here you go!
> 
${color7}WEATHER${hr 2}$color

${color}Location: Trenton, NJ

${color #B3B3B3}Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC}
Temperature: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 -i}
Forecast: ${execi 3600 python ~/scripts/conkyForecast.py --startday=0 --location=08628 --datatype=HT -i}/${execi 3600 python ~/scripts/conkyForecast.py --location=08628  --startday=0 --datatype=LT -i}
Humidity: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=HM}
Wind: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=WS -i}
${alignr}${voffset -58}${offset -70}${font weather:size=45}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=WF}$font
${voffset 15}${color ffffff}3 day forecast
${voffset 7}${color #B3B3B3}${offset 13}${execi 3600 python ~/scripts/conkyForecast.py -w --location=08628 --startday=1 --endday=5 --datatype=DW --spaces=7}
${font weather:size=33}${offset 6}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --startday=1 --endday=5 --datatype=WF} $font
${execi 3600 python ~/scripts/conkyForecast.py --startday=1 --location=08628 --datatype=HT -i}/${execi 3600 python ~/scripts/conkyForecast.py --location=08628 -n --startday=1 --datatype=LT -i}  ${execi 3600 python ~/scripts/conkyForecast.py --startday=2 --location=08628 --datatype=HT -i}/${execi 3600 python ~/scripts/conkyForecast.py --location=08628 -n --startday=2 --datatype=LT -i}  ${execi 3600 python ~/scripts/conkyForecast.py --startday=3 --location=08628 --datatype=HT -i}/${execi 3600 python ~/scripts/conkyForecast.py --location=08628 -n --startday=3 --datatype=LT -i}  ${execi 3600 python ~/scripts/conkyForecast.py --startday=4 --location=08628 --datatype=HT -i}/${execi 3600 python ~/scripts/conkyForecast.py --location=08628 -n --startday=4 --datatype=LT -i}  ${execi 3600 python ~/scripts/conkyForecast.py --startday=5 --location=08628 --datatype=HT -i}/${execi 3600 python ~/scripts/conkyForecast.py --location=08628 -n --startday=5 --datatype=LT -i}


It is very sloppy right now but it does the trick.  It would be shortened with a HT/LT combined command.

---

### Post by kaivalagi on 2008-04-21
> **yousillygoose said:**
> a quick note: i didn't see anyone say this but if they did i appologize for repeating.  I think having a function for HT/LT would be useful.  I am using your startday and endday definitions.  I cannot do this for HT and LT if I want to have it in the HT/LT format because the output would be:

HT HT HT HT HT / LT LT LT LT LT

Any thoughts?

Sounds like we need a HL datatype  :)

I'll get busy in the next couple of days - the working week is here again :(

---

### Post by moore.bryan on 2008-04-21
can someone shed some light on my little issue of the strange character before my degree symbol?

---

### Post by mokkurkalve on 2008-04-21
> **moore.bryan said:**
> can someone shed some light on my little issue of the strange character before my degree symbol?
Test if putting **[COLOR="Blue"]override_utf8_locale yes[/COLOR]** in .conkyrc helps...

---

### Post by moore.bryan on 2008-04-21
> **mokkurkalve said:**
> Test if putting **[COLOR=Blue]override_utf8_locale yes[/COLOR]** in .conkyrc helps...
excellent! didn't even think of this!!!

---

### Post by yousillygoose on 2008-04-21
Another comment:




[http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39)


Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC}
Tonight: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC -n}


Both of these are returning the condition as cloudy.  That page classifies it as partly and mostly cloudy for each one.  Is it pulling in inaccurate weather data for conditions?

---

### Post by kaivalagi on 2008-04-21
> **yousillygoose said:**
> Another comment:




[http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39)


Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC}
Tonight: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC -n}


Both of these are returning the condition as cloudy.  That page classifies it as partly and mostly cloudy for each one.  Is it pulling in inaccurate weather data for conditions?

The CC option drives the webserivces' condition code to conky textual output, the codes are assigned text and may well be a little off. I pinched the code to text relationship from the weather applet in AWN.

If you only require english output you can use the CT option instead. It is the text "as is" from the webservice and will most definitely be correct.

I'll do some digging to see if I can find the correct code to text relationships somewhere....starting with the weather.com website :)

Another item to add to the TODO list :)

---

### Post by yousillygoose on 2008-04-21
Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CT}
Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC}
Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CT -n}
Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC -n}

All of these are returning Mostly Cloudy.  When I refer to [http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39) it says that today it is code 44, or partly cloudy, and tonight it is 29 or partly cloudy.  Any other suggestions?

---

### Post by kaivalagi on 2008-04-21
> **yousillygoose said:**
> Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CT}
Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC}
Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CT -n}
Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC -n}

All of these are returning Mostly Cloudy.  When I refer to [http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/08628?dayf=5&prod=xoap&par=1048871467&key=12daac2f3a67cb39) it says that today it is code 44, or partly cloudy, and tonight it is 29 or partly cloudy.  Any other suggestions?

The only thing I can think of is that what you are looking at from the website is newer than what the script is using...

Try deleting the cached data (it may be out of date)

```
rm /tmp/conkyForecast*
```

When you run it again it will pickup new data and hopefully be the same :)

To increase the frequency for the web calls you need to reduce the values of the constants called EXPIRY_MINUTES_CURRENT (current data) and EXPIRY_MINUTES_FORECAST (forecasted data).

They are currently set to 240 minutes (4 hours)

---

### Post by yousillygoose on 2008-04-21
the data did change when i deleted the tmp.  It now both says cloudy.  The website still lists it as partly cloudy for both.  Any new ideas?

---

### Post by yousillygoose on 2008-04-21
I actually solved the problem.  I used --startday=0.  If i don't include that does it pull the data from somewhere else?  Either way it works now so my two lines are this:


Current


Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC --startday=0}

Tonight

Tonight: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CT -n --startday=0}

That does the trick  :)

---

### Post by yousillygoose on 2008-04-21
I'm sorry I post sooo frequently.  I like to think I'm helping in figuring the script out for the population (but really, I'm probably just annoying).  In your translation from condition number to weather font character some of them are different.  For example 29 and 44 both mean partly cloudy but you have them defined as different characters.  Is there a reason behind this?  Thank you so much for your hard work

---

### Post by kaivalagi on 2008-04-21
> **yousillygoose said:**
> I actually solved the problem.  I used --startday=0.  If i don't include that does it pull the data from somewhere else?  Either way it works now so my two lines are this:


Current


Condition: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CC --startday=0}

Tonight

Tonight: ${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --datatype=CT -n --startday=0}

That does the trick  :)

Have a look in the script, there are 2 url's used, the one with cc=* is current conditions :)

Any use of --startday will get the data from the forecast webservice url rather than current conditions equivalent.

I can't believe I didn't see that, should have noticed the url you provided :) I have my head in new development for the script at the mo so kinda distracted. What I'm working on should provide something useful for all...details in a couple of days :) I need to make sure it works first...

---

### Post by kaivalagi on 2008-04-21
> **yousillygoose said:**
> I'm sorry I post sooo frequently.  I like to think I'm helping in figuring the script out for the population (but really, I'm probably just annoying).  In your translation from condition number to weather font character some of them are different.  For example 29 and 44 both mean partly cloudy but you have them defined as different characters.  Is there a reason behind this?  Thank you so much for your hard work

Looks like an error, feel free to fix it up :) You'd be doing me a big favour!

 If you're up for it just PM me the resultant section of code for conditions_weather_font and I'll update the script on the thread...

Totally up to you

---

### Post by yousillygoose on 2008-04-21
surely, i'll tackle it for you.  It is the least I can do.

The only error I actually see is that 44 should be 'c'.  There are other flaws but I would guess that the flaws are in the weather font and not in the scripts.  For example, tornado and hurricane how the same symbol (w) but i would guess that this is due to the fonts.

---

### Post by kaivalagi on 2008-04-21
> **yousillygoose said:**
> surely, i'll tackle it for you.  It is the least I can do.

The only error I actually see is that 44 should be 'c'.  There are other flaws but I would guess that the flaws are in the weather font and not in the scripts.  For example, tornado and hurricane how the same symbol (w) but i would guess that this is due to the fonts.

I get the feeling that the condition_text from the CC option and the weather fonts output need some tweaking, but it's hard unless we have all the example weather to base a test on...

If only I knew how to create fonts...then we could have a font that displays all the icons we need. Any takers????

time to call it a night, catch up tomorrow...

---

### Post by yousillygoose on 2008-04-21
> **kaivalagi said:**
> I get the feeling that the condition_text from the CC option and the weather fonts output need some tweaking, but it's hard unless we have all the example weather to base a test on...

If only I knew how to create fonts...then we could have a font that displays all the icons we need. Any takers????

time to call it a night, catch up tomorrow...


Well I went through all of the characters to the weather font and they seem to be matched up as best as possible the way it is now.  You would have to compile a new .ttf with someone drawing new symbols (i suck with art or i would help you with it).  We only would need a few more symbols to symbolize tornados and such.

---

### Post by mojohn on 2008-04-21
Kaivalagi, I thought I had updated my conkyForecast.py your test conkyForecast.py and made appropriate changes to my .conkyrc. However, when I launch conky, the weather data isn't populated at all - but no errors or shown. See screenshot. 

Also, I uploaded my current conkyrc and conkyForecast. If you could point me to my errors, I would owe you a generous thanks!

Thanks,

mojohn

---

### Post by yousillygoose on 2008-04-21
> **mojohn said:**
> Kaivalagi, I thought I had updated my conkyForecast.py your test conkyForecast.py and made appropriate changes to my .conkyrc. However, when I launch conky, the weather data isn't populated at all - but no errors or shown. See screenshot. 

Also, I uploaded my current conkyrc and conkyForecast. If you could point me to my errors, I would owe you a generous thanks!

Thanks,

mojohn
 
you have an attachment of your config but it is not actually attached. If you attach it i can most likely help you

---

### Post by kaivalagi on 2008-04-22
> **mojohn said:**
> Kaivalagi, I thought I had updated my conkyForecast.py your test conkyForecast.py and made appropriate changes to my .conkyrc. However, when I launch conky, the weather data isn't populated at all - but no errors or shown. See screenshot. 

Also, I uploaded my current conkyrc and conkyForecast. If you could point me to my errors, I would owe you a generous thanks!

Thanks,

mojohn

The attached tar.gz has nothing in it (or atleast I don't see anything when I open it)

post you conkyrc contents in a code section and we'll take a look

---

### Post by moore.bryan on 2008-04-22
i run into this problem all the time with conky, but i'm hoping someone here can help... no matter how i set-up my .conkyrc, most things won't align properly (as seen in the attach). i also am posting my .conkyrc

---

### Post by yousillygoose on 2008-04-22
> **moore.bryan said:**
> i run into this problem all the time with conky, but i'm hoping someone here can help... no matter how i set-up my .conkyrc, most things won't align properly (as seen in the attach). i also am posting my .conkyrc


I have all of mine lined up nicely.  I have posted my config up above a few posts.  Some helpful commands ${offset} ${voffset} where they offset horizontally and vertically (respectively) and of course $alignr, $alignc, $alignl.  Your options are to first play with the --spaces=X option and replace X with a number.  If you can get that work combined with perhaps an align you will be lucky.  If not you can split the code up onto different lines and offset the output up and to the location you want.  With the offset commands you can put the data exactly where you'd like it so you can line things up perfectly.  Both positive and negative values can be accepted by offset.  Does this all make sense?

---

### Post by moore.bryan on 2008-04-22
> **yousillygoose said:**
> I have all of mine lined up nicely.  I have posted my config up above a few posts.  Some helpful commands ${offset} ${voffset} where they offset horizontally and vertically (respectively) and of course $alignr, $alignc, $alignl.  Your options are to first play with the --spaces=X option and replace X with a number.  If you can get that work combined with perhaps an align you will be lucky.  If not you can split the code up onto different lines and offset the output up and to the location you want.  With the offset commands you can put the data exactly where you'd like it so you can line things up perfectly.  Both positive and negative values can be accepted by offset.  Does this all make sense?
i'll try this stuff when i get a moment later... you did a great job explaining the offset rule/command/setting; however, i do have a question: why does the conky docs not talk about this setting? also, why in the world does conky have to be so complicated!?

---

### Post by yousillygoose on 2008-04-22
> **moore.bryan said:**
> i'll try this stuff when i get a moment later... you did a great job explaining the offset rule/command/setting; however, i do have a question: why does the conky docs not talk about this setting? also, why in the world does conky have to be so complicated!?



The conky docs/man files talk a little bit about all the different options conky has.  They can't go into all the options becauase the man file would be 100  pages long if they did.  They make conky as complicated as it is (in my opinion) so it is as highly tweakable.  Everyone can have a completely unique conky and it allows for much freedom (after taking some time to learn about it first of course).

---

### Post by moore.bryan on 2008-04-22
> **yousillygoose said:**
> They make conky as complicated as it is (in my opinion) so it is as highly tweakable.  Everyone can have a completely unique conky and it allows for much freedom (after taking some time to learn about it first of course).
i completely agree! i get the man page realism, but what about a website with ALL the options? maybe i'll become inspired and try to compile one...

---

### Post by kaivalagi on 2008-04-22
Hi All,

I have just updated the conkyForecast.py script to include new functionality, hopefully you'll find it useful :)

I have added the ability to use **template files** for output, so you can make a single exec call to get lots of formatted output returned.

I have tested the functionality fairly well but no doubt there will be a few issues with it, it is a little more complicated than anything done in the script before...but I am fairly confident it will work as required.

Please read the first post to get a feel for what this functionality entails and the limitations of it's setup. I have also included a test conkyrc and template file for this so you should have something good to start with.

Happy conking :)

---

### Post by yousillygoose on 2008-04-22
> **kaivalagi said:**
> Hi All,

I have just updated the conkyForecast.py script to include new functionality, hopefully you'll find it useful :)

I have added the ability to use **template files** for output, so you can make a single exec call to get lots of formatted output returned.

I have tested the functionality fairly well but no doubt there will be a few issues with it, it is a little more complicated than anything done in the script before...but I am fairly confident it will work as required.

Please read the first post to get a feel for what this functionality entails and the limitations of it's setup. I have also included a test conkyrc and template file for this so you should have something good to start with.

Happy conking :)



So I'm trying it out but still having some troubles with the template.

${execi 3600 python /home/yousillygoose/scripts/conkyForecast.py --location=UKXX0103 --template=/home/yousillygoose/scripts/conkyForecast.template} 

is the part in my conkyrc file.

In the template i put:
${color #B3B3B3}Condition: {--location=08628 --datatype=CC --startday=0}
Temperature: {--location=08628 -i}
Forecast: {--startday=0 --location=08628 --datatype=HT -i}/{--location=08628  --startday=0 --datatype=LT -i}
Humidity: {--location=08628 --datatype=HM}
Wind: {--location=08628 --datatype=WS -i}
Tonight: {--location=08628 --datatype=CT -n --startday=0}
${alignr}${voffset -100}${offset -70}${font weather:size=45}${color 3f689b}{--location=08628 --startday=0 --datatype=WF}$font$color
${alignr}${voffset 5}${offset -70}${font weather:size=45}${color 3f689b}{--location=08628 --startday=0 -n --datatype=WF}$font$color
${voffset 7}${color ffffff}3 day forecast
${voffset 7}${color #B3B3B3}${offset 13}{-w --location=08628 --startday=1 --endday=5 --datatype=DW --spaces=7}
${font weather:size=33}${color 3f689b}${offset 6}{--location=08628 --startday=1 --endday=5 --datatype=WF} $font$color
${color e0e0e0}{--startday=1 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=1 --datatype=LT -i}  {--startday=2 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=2 --datatype=LT -i}  {--startday=3 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=3 --datatype=LT -i}  {--startday=4 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=4 --datatype=LT -i}  {--startday=5 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=5 --datatype=LT -i}


but it doesn't work.  I also tried your sample template and it didn't work.  Any thoughts?

---

### Post by Yitram on 2008-04-22
> **yousillygoose said:**
> I have all of mine lined up nicely.  I have posted my config up above a few posts.  Some helpful commands ${offset} ${voffset} where they offset horizontally and vertically (respectively) and of course $alignr, $alignc, $alignl.  Your options are to first play with the --spaces=X option and replace X with a number.  If you can get that work combined with perhaps an align you will be lucky.  If not you can split the code up onto different lines and offset the output up and to the location you want.  With the offset commands you can put the data exactly where you'd like it so you can line things up perfectly.  Both positive and negative values can be accepted by offset.  Does this all make sense?


I think the alignment also depends on your resolution.  I copied your code in last night, and I ended up having to adjust things around to make them line up right.

Your code did still save me the trouble of having to figure out all the commands myself though, so it was still a help.


EDIT: Oooo, that will be a help.  I'll wait for goose to figure it out X-D

---

### Post by yousillygoose on 2008-04-22
> **yousillygoose said:**
> So I'm trying it out but still having some troubles with the template.

${execi 3600 python /home/yousillygoose/scripts/conkyForecast.py --location=UKXX0103 --template=/home/yousillygoose/scripts/conkyForecast.template} 

is the part in my conkyrc file.

In the template i put:
${color #B3B3B3}Condition: {--location=08628 --datatype=CC --startday=0}
Temperature: {--location=08628 -i}
Forecast: {--startday=0 --location=08628 --datatype=HT -i}/{--location=08628  --startday=0 --datatype=LT -i}
Humidity: {--location=08628 --datatype=HM}
Wind: {--location=08628 --datatype=WS -i}
Tonight: {--location=08628 --datatype=CT -n --startday=0}
${alignr}${voffset -100}${offset -70}${font weather:size=45}${color 3f689b}{--location=08628 --startday=0 --datatype=WF}$font$color
${alignr}${voffset 5}${offset -70}${font weather:size=45}${color 3f689b}{--location=08628 --startday=0 -n --datatype=WF}$font$color
${voffset 7}${color ffffff}3 day forecast
${voffset 7}${color #B3B3B3}${offset 13}{-w --location=08628 --startday=1 --endday=5 --datatype=DW --spaces=7}
${font weather:size=33}${color 3f689b}${offset 6}{--location=08628 --startday=1 --endday=5 --datatype=WF} $font$color
${color e0e0e0}{--startday=1 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=1 --datatype=LT -i}  {--startday=2 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=2 --datatype=LT -i}  {--startday=3 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=3 --datatype=LT -i}  {--startday=4 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=4 --datatype=LT -i}  {--startday=5 --location=08628 --datatype=HT -i}/{--location=08628 -n --startday=5 --datatype=LT -i}


but it doesn't work.  I also tried your sample template and it didn't work.  Any thoughts?


Note: I also tried it very simply with :
${execi 3600 python /home/yousillygoose/scripts/conkyForecast.py --location=08628 --template=/home/yousillygoose/scripts/conkyForecast.template} 

and 

Condition: {--datatype=CC --startday=0}


and this didn't work either.  Any help boss?

---

### Post by kaivalagi on 2008-04-22
> **yousillygoose said:**
> So I'm trying it out but still having some troubles with the template.


I definitely need to provide more examples and explanation of the template and how it works. Documentation was never my strong point :)

The template is **_not_** a replacement for the conky settings, it does not handle them. It can only handle options as you've used previously when calling the script, and only a subset of those. 

From the usage text the useable options inside curly braces are:
[LIST]
[*]--datatype
[*]--startday
[*]--endday
[*]--night
[*]--shortweekday
[*]--hideunits
[*]--imperial
[*]--spaces
[/LIST]

From the template notes section:

*"Note that you will not be able to combine standard font output with weather fonts in a single template. Font configuration is done inside the conkyrc file and so makes this impossible. A separate weather font based output can be generated and offsets can be used in the conkyrc to line up the data properly. Many of the "thread posters" can help in your offset endeavours I am sure."*

Looking at your template I've stripped out the bits that won't work, e.g. color options, location (done when calling the script itself), short form options like -i or -n don't work, use --imperial or --night, no offsets, no fonts, no aligns etc etc. See below. This has worked for me...

```
Condition: {--datatype=CC --startday=0}
Temperature: {--datatype=HT --imperial}
Forecast: {--startday=0 --datatype=HT --imperial}/{--startday=0 --datatype=LT --imperial}
Humidity: {--datatype=HM}
Wind: {--datatype=WS --imperial}
Tonight: {--datatype=CT --night --startday=0}
{--startday=0 --datatype=WF}
{--startday=0 --night --datatype=WF}
3 day forecast
{--shortweekdays --startday=1 --endday=5 --datatype=DW --spaces=7}
{--startday=1 --endday=5 --datatype=WF}
{--startday=1 --datatype=HT --imperial}/{--night --startday=1 --datatype=LT --imperial}  {--startday=2 --datatype=HT --imperial}/{--night --startday=2 --datatype=LT --imperial}  {--startday=3 --datatype=HT --imperial}/{--night --startday=3 --datatype=LT --imperial}  {--startday=4 --datatype=HT --imperial}/{--night --startday=4 --datatype=LT --imperial}  {--startday=5 --datatype=HT --imperial}/{--night --startday=5 --datatype=LT --imperial}
```

As mentioned in the first post on this thread, weather font based output can't be combined with the other output in a single template as it requires a font change, which is not something handleable outside of the conkyrc itself. Based on this, the above working template having weather font output is kinda useless. What needs to happen instead is, as done with the weather revisited perl script, you need to generate 2 sets of output, one textual and one for weather fonts, and use offsets in the conkyrc file to line them up. Bruce M knows all about this and there will be posts in the old perl based forum on this type of thing too I would imagine.

Do me a favour and copy the conkyForecast.py and conkyForecast.template files to /tmp/ and then run the following in your conkyrc:
${execi 3600 python /tmp/conkyForecast.py --location=08628 --template=/tmp/conkyForecast.template}

If that fails, I am thinking it may be permissions , give read access to both files for yourself (chmod a+r /tmp/conkyForecast*)

---

### Post by kaivalagi on 2008-04-22
> **yousillygoose said:**
> Note: I also tried it very simply with :
${execi 3600 python /home/yousillygoose/scripts/conkyForecast.py --location=08628 --template=/home/yousillygoose/scripts/conkyForecast.template} 

and 

Condition: {--datatype=CC --startday=0}


and this didn't work either.  Any help boss?

On the face of it all seems okay...you've definately got the template file in the path indicated? try creating a new file, pasting in the content and saving first...I'm stumped

Like I said I got your previous template working fine after I removed the stuff that won't work...

What errors do you get if you just run the python command in the terminal e.g. python /home/yousillygoose/scripts/conkyForecast.py --location=08628 --template=/home/yousillygoose/scripts/conkyForecast.template

???

---

### Post by yousillygoose on 2008-04-22
i'll give it a whirl.  It makes sense but now will take some time to make it all work.  The advantage of this would be to have less exec calls and in turn be able to have the script loop itself more often without burning too much cpu power.

This template may be useful for me simply for the H/L option (and not have 10 exec calls when i can simply use one.  I will give it a try and see what i can do

---

### Post by kaivalagi on 2008-04-22
> **yousillygoose said:**
> i'll give it a whirl.  It makes sense but now will take some time to make it all work.  The advantage of this would be to have less exec calls and in turn be able to have the script loop itself more often without burning too much cpu power.

This template may be useful for me simply for the H/L option (and not have 10 exec calls when i can simply use one.  I will give it a try and see what i can do

Great

Once we've got somewhere with this I wouldn't mind trying to get the help on the first post up to scratch. If you get it working can you post the steps you took please?

In the meantime, I'm going to try and get it working with 2 exec calls for the traditional weekdays/weather font and hi/lo combo...

---

### Post by yousillygoose on 2008-04-22
It works like a charm.  Thanks for the clarification on the syntax.  I feel like I can now also help people on this issue  :).  I now have a template for H/L weather format if anyone is interested  :).  I have the same conky i had before but now with 9 less exec's.

---

### Post by kaivalagi on 2008-04-22
> **yousillygoose said:**
> It works like a charm.  Thanks for the clarification on the syntax.  I feel like I can now also help people on this issue  :).  I now have a template for H/L weather format if anyone is interested  :).  I have the same conky i had before but now with 9 less exec's.

result!

At some point I'll create a test-template with more content, to show all possible setups...

The best thing about this is it doesn't limit you to any particular arrangement (other than font/color setting you might want in the conkyrc).

Should make for some interesting conky configs...

Next problem, re-posting this thread again in the new sections of the forum (if it doesn't go down again :) )

---

### Post by yousillygoose on 2008-04-22
haha, big false alarm boss.

It is giving me the output in the right format but with one problem.  I use imperial (F) and it is giving me the Celsius output with the F ending to it.  Basically it is labeling metric output with imperial symbols.  Any thoughts?

Edit:

I fixed my own problem.  You make not know this either  :).  For imperial data you need to throw the --imperial and --location=XXXXX in both the template and the .conkyrc where it calls the template or it confuses the data

---

### Post by yousillygoose on 2008-04-22
For a recap here is my .conkyrc, template, and screenshot.  Enjoy.

.conkyrc

> Text
${font size = 12}${time %B %d %G} ${color e0e0e0}${font}${voffset -1}${color}
${font size = 12}UpTime: ${color e0e0e0}${uptime_short}${color}$font

${color #718A96}SYSTEM ${color #94BCD1}${hr 2}$color
$nodename   $sysname 
$kernel  on $machine
Battery: ${color e0e0e0}${font}$battery${color e0e0e0}${font}${battery_time}

CPU:${color ffffff} Intel(R) Core(TM)2 Duo CPU @ 2.20GHz${color}
Cpu 1: ${color e0e0e0}${font}${cpu cpu1}% ${color e0e0e0}(${freq cpu1}MHz -- ${execi 8 sensors | grep -A 1 'Core 0' | cut -c15-16 | sed '/^$/d'}C)${color}
${color #5252FF}${cpubar cpu1}${color}
Cpu 2: ${color e0e0e0}${font}${cpu cpu2}% ${color e0e0e0}(${freq cpu2}MHz -- ${execi 8 sensors | grep -A 1 'Core 1' | cut -c15-16 | sed '/^$/d'}C) ${color}
${color #5252FF}${cpubar cpu2}$color
Load: ${color ffffff}$loadavg$color
Mem: ${color e0e0e0}${font}${mem} ${color}${color}
${color #5252FF}${membar 6}$color$color

${color #718A96}HDD ${color #94BCD1}${hr 2}$color
ROOT: ${color lightgrey}${fs_used_perc /}% -  ${fs_used /}/${fs_size /}${color}
    ${color slate grey}Temp: ${color lightgrey} ${execi 30 nc localhost 7634 | cut -c 24-25} C${color}
${color #5252FF}${fs_bar 6 /}$color
F DRIVE: ${color lightgrey}${fs_used_perc /media/F Drive}% -  ${fs_used /media/F Drive} / ${fs_size /media/F Drive}
${color #5252FF}${fs_bar 6 /media/F Drive}$color
H Drive: ${color lightgrey}${fs_used_perc /media/H Drive}% -  ${fs_used /media/H Drive} / ${fs_size /media/H Drive}
${color #5252FF}${fs_bar 6 /media/H Drive}$color

${color #718A96}VIDEO ${color #94BCD1}${hr 2}$color
${color lightgrey}Card: ${execi 30 nvidia-settings -q gpus | cut -c27-42 | sed '/^$/d'}
${color lightgrey}GPU: ${execi 30 nvclock -i | grep 'Architecture:' | cut -c16-19} @ ${execi 30 nvclock -i | grep 'GPU clock:' | cut -c13-23}
${color lightgrey}Mem: ${execi 30 /home/yousillygoose/Desktop/Downloads/nvclock0.8b3a/src/nvclock -i | grep 'Amount:' | cut -c10-15} ${execi 30 /home/yousillygoose/Desktop/Downloads/nvclock0.8b3a/src/nvclock -i | grep 'Type:' | cut -c17-20} @ ${execi 30 /home/yousillygoose/Desktop/Downloads/nvclock0.8b3a/src/nvclock -i | grep 'Clock: 5' | cut -c8-18}
${color lightgrey}GPU Temp: ${execi 30 nvidia-settings -q gpucoretemp |grep '):' | cut -c 42-43} C

${color #718A96}Net ${color #94BCD1}${hr 2}$color

IP:  ${addr eth0}
${color}${color e0e0e0}${font}${downspeed eth0}Kb/s ${color} ${totaldown eth0} Downloaded 
${color}${color e0e0e0}${upspeed eth0}Kb/s ${color} ${totalup eth0} Uploaded${color}${color} 

${color7}WEATHER${hr 2}$color

${color}Location: ${color ffffff}Trenton, NJ$color

${color #B3B3B3}${execi 3600 python /home/yousillygoose/scripts/conkyForecast.py --location=08628 --imperial --template=/home/yousillygoose/scripts/conkyForecast2.template}
${alignr}${voffset -130}${offset -70}${font weather:size=45}${color 3f689b}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --startday=0 --datatype=WF}$font$color
${alignr}${voffset 5}${offset -70}${font weather:size=45}${color 3f689b}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --startday=0 -n --datatype=WF}$font$color
${voffset 7}${color ffffff}3 day forecast
${voffset 7}${color #B3B3B3}${offset 15}${execi 3600 python ~/scripts/conkyForecast.py -w --location=08628 --startday=1 --endday=5 --datatype=DW --spaces=7}
${font weather:size=33}${color 3f689b}${offset 14}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --startday=1 --endday=5 --datatype=WF} $font$color
${color e0e0e0}${execi 3600 python /home/yousillygoose/scripts/conkyForecast.py --location=08628 --imperial --template=/home/yousillygoose/scripts/conkyForecast.template}

template file for current weather

> Condition: {--location=08628 --datatype=CC --startday=0}
Temperature: {--datatype=HT --location=08628 --imperial}
Forecast: {--startday=0 --datatype=HT --location=08628 --imperial}/{--startday=0 --datatype=LT --location=08628 --imperial}
Humidity: {--datatype=HM --location=08628}
Wind: {--datatype=WS --location=08628 --imperial}
Tonight: {--datatype=CT --night --location=08628 --startday=0}

template file for H/L weather

> {--startday=1 --location=08628 --datatype=HT --imperial}/{--location=08628 -n --startday=1 --datatype=LT --imperial}  {--startday=2 --location=08628 --datatype=HT --imperial}/{--location=08628 -n --startday=2 --datatype=LT --imperial}  {--startday=3 --location=08628 --datatype=HT --imperial}/{--location=08628 -n --startday=3 --datatype=LT --imperial}  {--startday=4 --location=08628 --datatype=HT --imperial}/{--location=08628 -n --startday=4 --datatype=LT --imperial}  {--startday=5 --location=08628 --datatype=HT --imperial}/{--location=08628 -n --startday=5 --datatype=LT --imperial}

There you go. I hope this helps and am glad to take questions to take some heat off of our nice script writer.  I don't belive i can simplify this more into more templates because they can't do weather fonts correctly.  ENjoys

---

### Post by kaivalagi on 2008-04-22
> **yousillygoose said:**
> haha, big false alarm boss.

It is giving me the output in the right format but with one problem.  I use imperial (F) and it is giving me the Celsius output with the F ending to it.  Basically it is labeling metric output with imperial symbols.  Any thoughts?

Edit:

I fixed my own problem.  You make not know this either  :).  For imperial data you need to throw the --imperial and --location=XXXXX in both the template and the .conkyrc where it calls the template or it confuses the data

You're right, I just looked at the script and it doesn't make sense to support --imperial in the template at all. The --imperial option defines the source data used to get all the data, which happens before any output formatting based on the template, so it needs to be in the conkyrc settings only. I'll amend the script, template and help tomorrow on this.

Once that's done you can remove --imperial from the template all together.

I use metric, hence not noticing the problem

[COLOR="Blue"]**Edit** - script and help text updated. If you use --imperial in a template it will just get ignored now, only the --imperial option used in the conkyrc will get used....I am calling it a night now :)[/COLOR]

---

### Post by mokkurkalve on 2008-04-22
> **moore.bryan said:**
> i completely agree! i get the man page realism, but what about a website with ALL the options? maybe i'll become inspired and try to compile one...

For conky options try this:
[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

I had to fiddle a bit to get stuff aligned like I wanted to,
but using conky options ${offset X} and ${voffset X} 
(and as mentioned before in this thread, there are several for aligning text, check the list)
and also the option --spaces=X provided by the script itself, it turned out nice. 
It's useful to note that --spaces=X also will take all kinds of numbers, including negative ones.
Useful ones could be -1, 0, 1, 2, 3 etc.

Conky also let you choose arbitrary fonts, so there's a lot you can do....

But for perfect alignment of output the script would have to offer some kind of 
padding option, but I guess this might be hard to code into a phyton script (?)
With padding I mean something like you could choose something along:
"If output of Z are less than four chars long, pad Z with spaces to make a total of four chars"

---

### Post by mojohn on 2008-04-22
Here it is - the files are there this time!

mojohn

---

### Post by kaivalagi on 2008-04-23
> **mojohn said:**
> Here it is - the files are there this time!

mojohn

The location code (USM00519) doesn't work 

Where do you want weather for? Did you get the code from the search url mentioned in the first post?

I just manually went to the page the script would use:
[http://xoap.weather.com/weather/local/USM00519?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/USM00519?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39)

and got:

<?xml version="1.0" encoding="ISO-8859-1"?>
<error>
  <err type="2">Invalid location provided.</err>
</error>

I'll try to handle the error better in the script...on the todo list

[COLOR="Blue"]Edit: You should now get a printed "Invalid location provided" when a location code is wrong...[/COLOR]

---

### Post by martynp on 2008-04-23
Hi Mate,

Good job on the templates.....

I hate to be different but I like my weather presented in metric for the temperature and imperial for the wind speed. It would appear that this is now not possible after your recent changes.

Any ideas?

Many Thanks

---

### Post by kaivalagi on 2008-04-23
> **martynp said:**
> Hi Mate,

Good job on the templates.....

I hate to be different but I like my weather presented in metric for the temperature and imperial for the wind speed. It would appear that this is now not possible after your recent changes.

Any ideas?

Many Thanks

Currently the xoap service xml is loaded into a class upfront based on the --imperial flag being there or not, so there is no ability to have mixed units (unlike my initial pymetar based script). 

The web service would need 2 calls for forecast data, as the url defines whether the results are metric or imperial. This would also mean the script needs to prepare 2 lots of the same data, which would slow it down quite a bit.

For now the answer is "this isn't possible".

When I get back to my PC at home I'll see whether there are any alternatives.

I guess I could add a conversation function for C to F and kph to mph, which could be triggered by a --imperial in the template options...and we always retreive the metric values from the website...

I'll take a look tonight :)

---

### Post by yousillygoose on 2008-04-23
I have another request that may be helpful but not sure if it is possible.  I use your script, as you have seen, both for current and forecasting data.  My problem is that if I use the 240 minutes for current weather it becomes outdated fast.  Is there any way to make an option for the expire and refresh time for the data?  If we do it this way I can keep my forecasting data from refreshing frequently and only refresh my current condition and temperature a lot.

---

### Post by kaivalagi on 2008-04-23
> **yousillygoose said:**
> I have another request that may be helpful but not sure if it is possible.  I use your script, as you have seen, both for current and forecasting data.  My problem is that if I use the 240 minutes for current weather it becomes outdated fast.  Is there any way to make an option for the expire and refresh time for the data?  If we do it this way I can keep my forecasting data from refreshing frequently and only refresh my current condition and temperature a lot.

The expiry options are in 2 parts, 1 for current and 1 for forecast. In theory you could reduce the current conditions expiry to 1 minute and leave the forecast at 240 minutes...this should result in the behaviour you want I think. To do this you will need to look for a all caps settings called EXPIRY_MINUTES something or other in the script itself...

Let me know how it goes, I'll update the help to detail the expiry options based on the outcome.

---

### Post by martynp on 2008-04-23
Hi,

Re the mixed imperial and metric figures....

Thanks for your reply.... I look forward to seeing if you can fix it?

Many Thanks

Martyn

---

### Post by Yitram on 2008-04-23
> **mojohn said:**
> Here it is - the files are there this time!

mojohn

> **kaivalagi said:**
> The location code (USM00519) doesn't work 

Where do you want weather for? Did you get the code from the search url mentioned in the first post?

I just manually went to the page the script would use:
[http://xoap.weather.com/weather/local/USM00519?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39](http://xoap.weather.com/weather/local/USM00519?cc=*&prod=xoap&par=1048871467&key=12daac2f3a67cb39)

and got:

<?xml version="1.0" encoding="ISO-8859-1"?>
<error>
  <err type="2">Invalid location provided.</err>
</error>

I'll try to handle the error better in the script...on the todo list

Since you are in the US, try using your zip code for the code, thats what I currently have and it works fine

---

### Post by kaivalagi on 2008-04-23
> **martynp said:**
> Hi,

Re the mixed imperial and metric figures....

Thanks for your reply.... I look forward to seeing if you can fix it?

Many Thanks

Martyn

I have now implemented unit conversation in the template so the following can be done:

```
{--datatype=LT --startday=1 --imperial}    {--datatype=HT --startday=2}/{--datatype=LT --startday=2}   {--datatype=HT --startday=3 --hideunits}/{--datatype=LT --startday=3 --hideunits}
```

The options available to use in the template are no longer applicable in the command line, when a template option is being used...it was one or the other

This way more flexibility is available :)

---

### Post by martynp on 2008-04-23
Hi,

Thanks for this.... I will try it tomorrow but I am sure it will be fine.


Thanks again

Martyn

---

### Post by kaivalagi on 2008-04-23
I thought I'd post my conky setup

I am using a template to get weather data in one call, and calling again for the weather font output twice...3 execi calls in all for my weather output.

I've attached my conkyrc and the template file it refers to.

No doubt the layout needs adjusting for any font changes, and really I should probably use mono fonts to ensure the layout is always neat and tidy...time will tell what I need to do w.r.t. fonts etc

Hopefully this is a starter for most when it comes to a working usable conkyForecast template anyway

Enjoy :)

---

### Post by kaivalagi on 2008-04-23
> **martynp said:**
> Hi,

Thanks for this.... I will try it tomorrow but I am sure it will be fine.


Thanks again

Martyn

I am using --imperial for wind speed and metric for temperature in my conky posting, so it does work ;)

---

### Post by Bruce M. on 2008-04-23
Hi Folks,

Spent a good portion of today converting my conky weather from conkyForecast.py "Version 1" to the latest version. With some configuration changes as well. Did realise that the format for the command line had changed but I found out.

I decided not to use a weather font in my "main" conky as the "viewable" sizes of the fonts are different sizes. The smallest being the "Sun" symbol and the largest that I know of is the "Thunderstorm/Lightning" symbol. It meant tweaking every now and then.

So here's my 3 day "horizontal" weather forecast.

conky weather - English version:
```
TEXT
${color lightblue}From:${color} Buenos Aires, Argentina
${color lightblue}Lat: ${color orange}34°35'S  ${color lightblue}Long: ${color orange}58°21'W ${alignr} ${color lightblue}Alt: ${color orange}25 m$color                        
${voffset 5}${color lightblue}Now: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC}${alignr 2}${color lightblue}Wind: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS} ${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WD}${color}
${font Zekton:size=25}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT}${font}${alignr 2}${voffset -22}${color lightblue}Humidity: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM}
${alignr 2}${voffset 3}${color lightblue}Precipitation: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC --startday=0}${color}
${hr 1}
${voffset 5}${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=DW --startday=1}: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC --startday=1}${alignr 2}${color lightblue}Wind: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS --startday=1} ${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WD --startday=1}${color}
${font Zekton:size=14}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT --startday=1} ${color lightblue}/${color} ${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=LT --startday=1}${font}${alignr 2}${voffset -7}${color lightblue}Humidity: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM --startday=1}
${alignr 2}${color lightblue}Precipitation: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC --startday=1}${color}
${hr 1}
${voffset 5}${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=DW --startday=2}: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC --startday=2}${alignr 2}${color lightblue}Wind: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS --startday=2} ${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WD --startday=2}${color}
${font Zekton:size=14}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT --startday=2} ${color lightblue}/${color} ${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=LT --startday=2}${font}${alignr 2}${voffset -7}${color lightblue}Humidity: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM --startday=2}
${alignr 2}${color lightblue}Precipitation: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC --startday=2}${color}
```
Conky weather - Spanish version:
```
${color lightblue}Desde:${color} Buenos Aires, Argentina
${color lightblue}Lat: ${color orange}34°35'S  ${color lightblue}Long: ${color orange}58°21'W ${alignr} ${color lightblue}Alt: ${color orange}25 m$color
${voffset 5}${color lightblue}Hoy: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC --locale=es}${alignr 2}${color lightblue}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS --locale=es} ${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WD}${color}
${font Zekton:size=25}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT}${font}${alignr 2}${voffset -22}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM --locale=es}
${alignr 2}${voffset 3}${color lightblue}Precipitación: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC --startday=0 --locale=es}${color}
${hr 1}
${voffset 5}${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=DW --startday=1 --locale=es}: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC --startday=1 --locale=es}${alignr 2}${color lightblue}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS --startday=1} ${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WD --startday=1 --locale=es}${color}
${font Zekton:size=14}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT --startday=1} ${color lightblue}/${color} ${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=LT --startday=1}${font}${alignr 2}${voffset -7}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM --startday=1}
${alignr 2}${color lightblue}Precipitación: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC --startday=1}${color}
${hr 1}
${voffset 5}${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=DW --startday=2 --locale=es}: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC --startday=2 --locale=es}${alignr 2}${color lightblue}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS --startday=2} ${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WD --startday=2 --locale=es}${color}
${font Zekton:size=14}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT --startday=2} ${color lightblue}/${color} ${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=LT --startday=2}${font}${alignr 2}${voffset -7}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM --startday=2}
${alignr 2}${color lightblue}Precipitación: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC --startday=2}${color}

```
And the every famous, what we all want to see, attachment.

CHIMO!
Bruce

---

### Post by TB2 on 2008-04-23
Another suggestion:

If I'm taking the notebook with me and if I don't have an internet connection at boot time, conky will of course start nevertheless, but it will take very long and finally the wohle weather part will be distorted and ugly because full lines of "no connection" errors and the whole of conky will get wider and it's a total mess.

It would be great if you could implement an "offline friendly" option that will eighter
A) display the last known values or maybe
B) display a default symbol if the weather font is needed (e.g. sunny) but print something like "unknown" or "disconnected" for written out values like conditions and stuff and something like "X° C" for temperatures. The thing that's printed should resemble the wanted value in size and appearance.

This way conky would remain tidy even if you're booting without a network connection present.

Thanks again for your work!

---

### Post by martynp on 2008-04-24
Hi,

Had chance to play with this and it is great. However I am having some trouble with formatting.

You can see from the screenshot that I am working on getting a 7-day horizontal forecast but have hit a wall. No matter what I do I cannont get the template to put any more data on the screen.

I intended to continue down the table with Low Temps, Wind Speed etc but just can't get anymore out of it.

Please see attached screenshot and template.

Any help greatly appreciated.

Many Thanks,

Martyn

---

### Post by kaivalagi on 2008-04-24
> **martynp said:**
> Hi,

Had chance to play with this and it is great. However I am having some trouble with formatting.

You can see from the screenshot that I am working on getting a 7-day horizontal forecast but have hit a wall. No matter what I do I cannont get the template to put any more data on the screen.

I intended to continue down the table with Low Temps, Wind Speed etc but just can't get anymore out of it.

Please see attached screenshot and template.

Any help greatly appreciated.

Many Thanks,

Martyn

I think you've hit a limit with conky? :shock:

If you run the python script with your template outside of conky i.e.
 
```

python /home/mark/scripts/conkyForecast.py --location=UKXX0103 --template=/home/mark/scripts/conkyForecast.template
```

you get the full output:

```
 Fri        Sat       Sun      Mon      Tue      Wed     Thu


 17°       18°       17°       14°       12°       11°     13°


8°       9°       7°       6°       4°       4°     5°

```

Can anyone else test Martynp's template in conky, is the output cut short for you too?

Sounds like we might need to request a conky mod, to cater for a larger size output string from exec calls...

---

### Post by kaivalagi on 2008-04-24
> **TB2 said:**
> Another suggestion:

If I'm taking the notebook with me and if I don't have an internet connection at boot time, conky will of course start nevertheless, but it will take very long and finally the wohle weather part will be distorted and ugly because full lines of "no connection" errors and the whole of conky will get wider and it's a total mess.

It would be great if you could implement an "offline friendly" option that will eighter
A) display the last known values or maybe
B) display a default symbol if the weather font is needed (e.g. sunny) but print something like "unknown" or "disconnected" for written out values like conditions and stuff and something like "X° C" for temperatures. The thing that's printed should resemble the wanted value in size and appearance.

This way conky would remain tidy even if you're booting without a network connection present.

Thanks again for your work!

Option 1 I think

i.e. If (last known values expired) and (got a connection) then (fetch the data) otherwise (load last known values)

This will rely on you having a connection to the internet atleast initially so you'll have data from before, to use again.

Sounds like a plan to you?
[COLOR="Blue"]
Edit: See development history in first post for today...handling for no connectivity in place, just make sure you've connected atleast once :)[/COLOR]

---

### Post by martynp on 2008-04-24
Hi,

Thanks for the quick reply...... I sort of guessed that might be the case!

I was getting all this info nicely formatted pre your template but obviously that involved about a gazillion exec calls.

I'll monitor for a fix.

Many Thanks again

---

### Post by moore.bryan on 2008-04-24
so, none of the weather information is correct even though my location is... well, that's not entirely true; when i compare my wind-speed to noaa it's correct.

any ideas?

---

### Post by kaivalagi on 2008-04-24
> **moore.bryan said:**
> so, none of the weather information is correct even though my location is... well, that's not entirely true; when i compare my wind-speed to noaa it's correct.

any ideas?

Sorry, I don't understand what you mean. Are you saying the weather.com feed is not accurate?? my metric to imperial conversations are not right? 

????

Example script call, template if used, output...

Are you using the correct location code based on the search url posted in the top post?

---

### Post by moore.bryan on 2008-04-24
> **kaivalagi said:**
> Sorry, I don't understand what you mean. Are you saying the weather.com feed is not accurate?? my metric to imperial conversations are not right? 

????

Example script call, template if used, output...

Are you using the correct location code based on the search url posted in the top post?
sorry for taking so long to respond; silly work. attached are thumbs... the location code is correct and i checked it four times for spelling errors.

---

### Post by kaivalagi on 2008-04-24
> **martynp said:**
> Hi,

Thanks for the quick reply...... I sort of guessed that might be the case!

I was getting all this info nicely formatted pre your template but obviously that involved about a gazillion exec calls.

I'll monitor for a fix.

Many Thanks again

There is a conky config to allow larger amounts of data returned from scripts.

The config is "text_buffer_size", the default being 128 bytes

If you put the following in your conkyrc (before the TEXT section) it should hopefully fix your problem:

```
text_buffer_size 256

```

Hope that helps

---

### Post by kaivalagi on 2008-04-24
> **moore.bryan said:**
> sorry for taking so long to respond; silly work. attached are thumbs... the location code is correct and i checked it four times for spelling errors.

Are you using --startday=0 for today?

I suspect you are retrieving forecast data for today and comparing to current conditions on the website....just a guess

The script allows fetching current conditions (no --startday option) or forecast data (for today and the next 7 days)

If none of this rings any bells then you gonna need to post your script call options (or conkyrc if you wish) and template if you are using one

Cheers

P.S. sneak in some conky/python time at work like I do :)

---

### Post by moore.bryan on 2008-04-24
no --startday=0, no startday string at all.

relevant conky code:
```

${color #ffffff}WEATHER
${offset 10}${color #ffffff}Location: ${color #e3701a}School
${offset 20}${color #ffffff}Current Conditions: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=CC --imperial}
${offset 20}${color #ffffff}Temperature: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=HT --imperial}
${offset 20}${color #ffffff}Forecast: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=HT --imperial}/${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --startday=0 --datatype=LT --imperial}
${offset 20}${color #ffffff}Humidity: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=HM --imperial}
${offset 20}${color #ffffff}Wind: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=WS --imperial}
${offset 10}${color #ffffff}Location: ${color #e3701a}Home
${offset 20}${color #ffffff}Current Conditions: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=CC --imperial}
${offset 20}${color #ffffff}Temperature: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=HT --imperial}
${offset 20}${color #ffffff}Forecast: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=HT --imperial}/${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --startday=0 --datatype=LT --imperial}
${offset 20}${color #ffffff}Humidity: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=HM --imperial}
${offset 20}${color #ffffff}Wind: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=WS --imperial}

```

---

### Post by kaivalagi on 2008-04-24
> **moore.bryan said:**
> no --startday=0, no startday string at all.

relevant conky code:
```

${color #ffffff}WEATHER
${offset 10}${color #ffffff}Location: ${color #e3701a}School
${offset 20}${color #ffffff}Current Conditions: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=CC --imperial}
${offset 20}${color #ffffff}Temperature: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=HT --imperial}
${offset 20}${color #ffffff}Forecast: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=HT --imperial}/${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --startday=0 --datatype=LT --imperial}
${offset 20}${color #ffffff}Humidity: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=HM --imperial}
${offset 20}${color #ffffff}Wind: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA0740 --datatype=WS --imperial}
${offset 10}${color #ffffff}Location: ${color #e3701a}Home
${offset 20}${color #ffffff}Current Conditions: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=CC --imperial}
${offset 20}${color #ffffff}Temperature: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=HT --imperial}
${offset 20}${color #ffffff}Forecast: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=HT --imperial}/${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --startday=0 --datatype=LT --imperial}
${offset 20}${color #ffffff}Humidity: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=HM --imperial}
${offset 20}${color #ffffff}Wind: ${color #e3701a}${execi 3600 python ~/.scripts/conkyForecast.py --location=USPA1277 --datatype=WS --imperial}

```

Everything looks fine...I am stumped to be honest

Do the figures match if you compare metric amounts (i.e. no --imperial options and metric output on website)

I recently made a change to always bring back metric data and convert to imperial internally...I wonder whether this is the cause? The temperature conversation might be wrong? I wouldn't test that much myself as I use metric...but it should work as it's the a standard formula.

Also if you use CT rather than CC is the condition text matching? The CC option derives text based on a condition code and is not delivered as text initially.

I would expect the XOAP service to be what's behind the weather.com main pages content to be honest, and therefore everything should line up...

Let's hope it's a cock up on my part and not bad data from weather.com...

---

### Post by moore.bryan on 2008-04-24
okay, so if i kill conky and restart it, everything's fine. at what interval does the script refresh?

---

### Post by kaivalagi on 2008-04-24
> **moore.bryan said:**
> okay, so if i kill conky and restart it, everything's fine. at what interval does the script refresh?

I am posting a fix very soon, I got the calculation wrong for Celsius to Fahrenheit, which will be why the figures are not lining up.

Give me 5 minutes and I'll have the fix uploaded anyway, so hold fire for the moment...

FYI, the script refreshes every 4 hours by default, which might explain things...you can edit the script to make only current conditions refresh faster, look for the EXPIRY_MINUTES_CURRENT = 240, and change it to say EXPIRY_MINUTES_CURRENT = 30

Cheers

[COLOR="Blue"]Edit: Uploaded fix for conversions of temp (when using --imperial option)[/COLOR]

---

### Post by moore.bryan on 2008-04-24
excellent! this is a great little script and you should be proud of your "baby."

---

### Post by kaivalagi on 2008-04-24
> **moore.bryan said:**
> excellent! this is a great little script and you should be proud of your "baby."

Thanks, I'm glad it fits the bill. My baby certainly is demanding :)

Seriously though, this has been a really good exercise for me, learning what can be done with python etc. If you don't know python and want to learn, have a look at the script, there is all sorts of code examples in there.

BTW, you might want to use a template with all the data you want to display...examples further up the thread :)

Enjoy

P.S. Any other conky script requests are welcome...

---

### Post by martynp on 2008-04-24
> **kaivalagi said:**
> There is a conky config to allow larger amounts of data returned from scripts.

The config is "text_buffer_size", the default being 128 bytes

If you put the following in your conkyrc (before the TEXT section) it should hopefully fix your problem:

```
text_buffer_size=256

```

Hope that helps

Hi,

Have added this to my .conkyrc and see no difference. I agree that you do get the full output when running the terminal.

Attached is my .conkyrc if you would like to check it.

Many Thanks,

Martyn

---

### Post by kaivalagi on 2008-04-24
> **martynp said:**
> Hi,

Have added this to my .conkyrc and see no difference. I agree that you do get the full output when running the terminal.

Attached is my .conkyrc if you would like to check it.

Many Thanks,

Martyn

I noticed you have a config "no_buffers yes", try commenting that out, it might be overriding the buffer size entry...

Failing that I suggest you comment out "out_to_console no" or set it to yes and see what is coming back to the console when you run conky...

---

### Post by martynp on 2008-04-24
> **kaivalagi said:**
> I noticed you have a config "no_buffers yes", try commenting that out, it might be overriding the buffer size entry...

Failing that I suggest you comment out "out_to_console no" or set it to yes and see what is coming back to the console when you run conky...

Thanks for the reply....

no change with no_buffers yes commented out.

set out_to_console to yes and see this:

 3: no such configuration: 'text_buffer_size=256' [COLOR="Red"]EDIT..... removed the '=' and it is working!

                                                               Will continue to format and see how it goes!![/COLOR]

Sorry to cause you a headache but it must be a challenge to fix it!!

Martyn

---

### Post by kaivalagi on 2008-04-24
> **martynp said:**
> Thanks for the reply....

no change with no_buffers yes commented out.

set out_to_console to yes and see this:

 3: no such configuration: 'text_buffer_size=256' [COLOR="Red"]EDIT..... removed the '=' and it is working!

                                                               Will continue to format and see how it goes!![/COLOR]

Sorry to cause you a headache but it must be a challenge to fix it!!

Martyn

It's all good. No problems, only solutions :)

If people are going to use the template method with this script then the buffer limitation will definitely be an obstacle, so needs attention.

Thanks for clearing the use of text_buffer_size up. I will add a mention to it in the top post!

---

### Post by Bruce M. on 2008-04-24
Three web pages I found absolutely necessary when I started using conky are:

[LIST=1]
[*] [~.conkyrc settings]("http://conky.sourceforge.net/config_settings.html")

[*] [Conky Variables]("http://conky.sourceforge.net/variables.html")

[*] [Conky Manual]("http://conky.sourceforge.net/docs.html")
[/LIST]

Maybe if we ask nice kaivalagi will put them at the bottom of Post #1 as a helpful reminder. Not really a part of the *Conky Weather Python Script* but hey, if you can't get conky running you can't use the script. And lets face it, we were all new to conky at one time.

CHIMO!

---

### Post by kaivalagi on 2008-04-24
> **Bruce M. said:**
> Three web pages I found absolutely necessary when I started using conky are:

[LIST=1]
[*] [~.conkyrc settings]("http://conky.sourceforge.net/config_settings.html")

[*] [Conky Variables]("http://conky.sourceforge.net/variables.html")

[*] [Conky Manual]("http://conky.sourceforge.net/docs.html")
[/LIST]

Maybe if we ask nice kaivalagi will put them at the bottom of Post #1 as a helpful reminder. Not really a part of the *Conky Weather Python Script* but hey, if you can't get conky running you can't use the script. And lets face it, we were all new to conky at one time.

CHIMO!

Done :grin:

---

### Post by mokkurkalve on 2008-04-24
When it comes to the EXPIRY_* variables, I live in a town with so much, or rather, so everchanging weather, that I first tought your script could hardly be parsing the correct data, until I changed those. Now I have put 60 for both of the EXPIRY_* variables, and 1800 as conky run time (every half hour) and it seems the data currently parsed are on par with the reality outside my window..... ;)

---

### Post by kaivalagi on 2008-04-25
> **mokkurkalve said:**
> When it comes to the EXPIRY_* variables, I live in a town with so much, or rather, so everchanging weather, that I first tought your script could hardly be parsing the correct data, until I changed those. Now I have put 60 for both of the EXPIRY_* variables, and 1800 as conky run time (every half hour) and it seems the data currently parsed are on par with the reality outside my window..... ;)

Glad to hear all is good, I really should have mentioned the expiry settings sooner...(I did on the old thread, but forgot here)

To stop any further concerns I think I'll alter the default expiry for current conditions to 30 minutes...at some point

---

### Post by moore.bryan on 2008-04-25
another "broad" question... are there two variables for the **current** temperature and the **forecasted** temperature?

---

### Post by kaivalagi on 2008-04-25
> **moore.bryan said:**
> another "broad" question... are there two variables for the **current** temperature and the **forecasted** temperature?

There is a LT (low) and HT (high) for forecast temperatures, these don't differ between day and night forecasts. They are for the whole 24 hour period.

For current conditions LT and HT are the same as there is only one "current" temp. It was just pointless having a third data type for current temp only.

I wanted to map both current and forecast weather data to the same data types, so had to do this really.

Does that answer your question?

Cheers

---

### Post by moore.bryan on 2008-04-25
> **kaivalagi said:**
> There is a LT (low) and HT (high) for forecast temperatures, these don't differ between day and night forecasts. They are for the whole 24 hour period.

For current conditions LT and HT are the same as there is only one "current" temp. It was just pointless having a third data type for current temp only.

I wanted to map both current and forecast weather data to the same data types, so had to do this really.

Does that answer your question?

Cheers
i'm not sure. here's what my thinking is: HT is for the forecasted high for any given day, LT is for the forecasted low for any given day, but what is for the current temperature? that number should not be the forecasted high for the day...

does that make sense?

---

### Post by kaivalagi on 2008-04-25
> **moore.bryan said:**
> i'm not sure. here's what my thinking is: HT is for the forecasted high for any given day, LT is for the forecasted low for any given day, but what is for the current temperature? that number should not be the forecasted high for the day...

does that make sense?

examples:

"python conkyForecast.py --location=ABXX1234 --datatype=HT --startday=0" [B]gives todays high temp
[/B]
"python conkyForecast.py --location=ABXX1234 --datatype=LT --startday=0" **gives todays low temp**

"python conkyForecast.py --location=ABXX1234 --datatype=HT" **_OR_** "python conkyForecast.py --location=ABXX1234 --datatype=LT" **gives the current temp**

HT or LT when no specified against a specific day (i.e. current) are the same data.

Makes sense now?

---

### Post by moore.bryan on 2008-04-25
> **kaivalagi said:**
> makes sense now?
yes! however, the HT it's reporting for one of my locations is wrong and the other is right... must be a weather.com issue. thanks, again, for your help!

---

### Post by kaivalagi on 2008-04-25
> **moore.bryan said:**
> yes! however, the HT it's reporting for one of my locations is wrong and the other is right... must be a weather.com issue. thanks, again, for your help!

You could try bringing your expiry settings down, it might be that that they've updated the forecast data and you are using 'old' data for conky as the expiry has not been reached...

Take a look at the first post for details on the expiry settings.

You could also use the --refetch option, this will force an update of the data every time the execi is fired in conky...

---

### Post by moore.bryan on 2008-04-25
> **kaivalagi said:**
> You could also use the --refetch option, this will force an update of the data every time the execi is fired in conky...
this did the trick... thanks!

---

### Post by Yitram on 2008-04-25
The only thing that I could think of that would be really cool, would, at night, instead of showing the standard Sun icon for 'Clear' it shows a moon instead.  I've looked through the weather text font, and I've seen moons in there.  Or is that already set up, because I just noticed that there's a nighttime thunderstorm icon that is showing up, so maybe you already added that in there :KS  Other than that, I can't complain about the script, and thanks for learning python, so the rest of us don't have to :-D

---

### Post by mokkurkalve on 2008-04-26
I haven't looked into the template stuff yet, so I'm using a lot of execi calls. Anyway I posted my conky setup today, so if anybody want to see how I've used conkyForecast.py, you can take a look at this posting:
[http://ubuntuforums.org/showpost.php?p=4798972&postcount=2283]("http://ubuntuforums.org/showpost.php?p=4798972&postcount=2283")

---

### Post by kaivalagi on 2008-04-26
> **Yitram said:**
> The only thing that I could think of that would be really cool, would, at night, instead of showing the standard Sun icon for 'Clear' it shows a moon instead.  I've looked through the weather text font, and I've seen moons in there.  Or is that already set up, because I just noticed that there's a nighttime thunderstorm icon that is showing up, so maybe you already added that in there :KS

Sounds like a cool idea, we'd need separate daytime/nighttime weather font lists for condition codes. If someone wants to setup the lists correctly and post them I can then go about having the weather font based also on the --night option :)

In fact, the weather font to condition code linking could do with a once over, I am sure some of the characters are setup wrong, so anyone out there who has time to burn, feel free to chip in...

You can use the condition code to text list (first array listed below) to understand what each code means, and then figure out what font character is required to be used for each code to display the correct weather font (and update the second array list).

So for example, currently code 0 = Tornado (from the conditions_text array below), and the weather font character defined for code 0 is "W" (from the conditions_weather_font array below).

The conditions_weather_font list would need to be duplicated and assigned different characters for night time display, before I can setup this in code.

If you want to help but need more instructions, let me know.

> **Yitram said:**
> I can't complain about the script, and thanks for learning python, so the rest of us don't have to :-D

It's really not too hard to learn, especially if your a developer already with a few languages under your belt :) next on the list is LISP...someday


```
	conditions_text = {
		"0": _(u"Tornado"),
		"1": _(u"Tropical Storm"),
		"2": _(u"Hurricane"),
		"3": _(u"Severe Thunderstorms"),
		"4": _(u"Thunderstorms"),
		"5": _(u"Mixed Rain and Snow"),
		"6": _(u"Mixed Rain and Sleet"),
		"7": _(u"Mixed Precipitation"),
		"8": _(u"Freezing Drizzle"),
		"9": _(u"Drizzle"),
		"10": _(u"Freezing Rain"),
		"11": _(u"Showers"),
		"12": _(u"Showers"),
		"13": _(u"Snow Flurries"),
		"14": _(u"Light Snow Showers"),
		"15": _(u"Blowing Snow"),
		"16": _(u"Snow"),
		"17": _(u"Hail"),
		"18": _(u"Sleet"),
		"19": _(u"Dust"),
		"20": _(u"Fog"),
		"21": _(u"Haze"),
		"22": _(u"Smoke"),
		"23": _(u"Blustery"), 
		"24": _(u"Windy"),
		"25": _(u"Cold"),
		"26": _(u"Cloudy"),
		"27": _(u"Mostly Cloudy"),
		"28": _(u"Mostly Cloudy"),
		"29": _(u"Partly Cloudy"),
		"30": _(u"Partly Cloudy"),
		"31": _(u"Clear"),
		"32": _(u"Clear"),
		"33": _(u"Fair"),
		"34": _(u"Fair"),
		"35": _(u"Mixed Rain and Hail"),
		"36": _(u"Hot"),
		"37": _(u"Isolated Thunderstorms"),
		"38": _(u"Scattered Thunderstorms"),
		"39": _(u"Scattered Thunderstorms"),
		"40": _(u"Scattered Showers"),
		"41": _(u"Heavy Snow"),
		"42": _(u"Scattered Snow Showers"),
		"43": _(u"Heavy Snow"),
		"44": _(u"Partly Cloudy"),
		"45": _(u"Thunder Showers"),
		"46": _(u"Snow Showers"),
		"47": _(u"Isolated Thunderstorms"),
		"na": _(u"N/A"),
		"-": _(u"N/A")
	}

	conditions_weather_font = {
		"0": _(u"W"),
		"1": _(u"V"),
		"2": _(u"W"),
		"3": _(u"s"),
		"4": _(u"p"),
		"5": _(u"k"),
		"6": _(u"k"),
		"7": _(u"g"),
		"8": _(u"g"),
		"9": _(u"g"),
		"10": _(u"h"),
		"11": _(u"g"),
		"12": _(u"g"),
		"13": _(u"k"),
		"14": _(u"k"),
		"15": _(u"k"),
		"16": _(u"k"),
		"17": _(u"k"),
		"18": _(u"k"),
		"19": _(u"e"),
		"20": _(u"e"),
		"21": _(u"a"),
		"22": _(u"d"),
		"23": _(u"d"), 
		"24": _(u"d"),
		"25": _(u"d"),
		"26": _(u"e"),
		"27": _(u"e"),
		"28": _(u"e"),
		"29": _(u"c"),
		"30": _(u"c"),
		"31": _(u"a"),
		"32": _(u"a"),
		"33": _(u"b"),
		"34": _(u"b"),
		"35": _(u"k"),
		"36": _(u"a"),
		"37": _(u"f"),
		"38": _(u"f"),
		"39": _(u"f"),
		"40": _(u"g"),
		"41": _(u"k"),
		"42": _(u"k"),
		"43": _(u"k"),
		"44": _(u"b"),
		"45": _(u"g"),
		"46": _(u"k"),
		"47": _(u"f"),
		"na": _(u"N/A"),
		"-": _(u"N/A")
	}

```

---

### Post by yousillygoose on 2008-04-26
i said in an earlier post, but the only one i saw was wrong was 44 ( i went through a lot of them)  Some of them aren't the best fitting icons but it is weather.ttf bottlenecking it, not the way the letters are assigned

---

### Post by yousillygoose on 2008-04-26
Quick question for you.  The weather script is making my conky window extend farther down my screen than it needs to.  The data ends in conky and it than outputs a bunch of spaces of emptyness expanding my conky a couple inches down my screen.  Any suggestions?

---

### Post by yousillygoose on 2008-04-26
I have learned that my problem revolves around :

${alignr}${voffset 5}${offset -70}${font weather:size=45}${color 3f689b}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --startday=0 -n --datatype=WF}$font$color


the output of the execi doesn't return many spaces so that isnt the problem.

I think the problem may be with the voffset and the offset.  Can anyone test it and tell me what happens.

The negative thing that happens to me is that the bottom of my conky window is expanded a few inches

---

### Post by kaivalagi on 2008-04-26
> **yousillygoose said:**
> I have learned that my problem revolves around :

${alignr}${voffset 5}${offset -70}${font weather:size=45}${color 3f689b}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --startday=0 -n --datatype=WF}$font$color


the output of the execi doesn't return many spaces so that isnt the problem.

I think the problem may be with the voffset and the offset.  Can anyone test it and tell me what happens.

Just ran the the below in a test conky file (same as you posted minus the color config as I couldn't see it on a blue background :) ):

```
${alignr}========== Previous Line ================
${alignr}${voffset 5}${offset -70}${font weather:size=45}${execi 3600 python ~/Projects/Weather/Weather.com/conkyForecast.py --location=08628 --startday=0 -n --datatype=WF}$font$color
${alignr}========== Next Line ================
```

And I get the attached screenshot...

Looks okay to me, could it be your other config settings in your conkyrc?

Edit: In case you need to know, I am currently running version 1.49 of conky, as I haven't gotten around to recompiling version 1.51 yet (need some non default compile options for xmms2 support so I don't use the repo's version)

---

### Post by yousillygoose on 2008-04-26
any chance you want to test the rest of my goodies??

For some reason the bottom of the window, while not visible, takes up more desktop than needed

---

### Post by Bruce M. on 2008-04-26
> **kaivalagi said:**
> 
```
${alignr}========== Previous Line ================
${alignr}${voffset 5}${offset -70}${font weather:size=45}${execi 3600 python ~/Projects/Weather/Weather.com/conkyForecast.py --location=08628 --startday=0 -n --datatype=WF}$font$color
${alignr}========== Next Line ================
```

And I get the attached screenshot...

Looks okay to me, could it be your other config settings in your conkyrc?

Edit: In case you need to know, I am currently running version 1.49 of conky, as I haven't gotten around to recompiling version 1.51 yet (need some non default compile options for xmms2 support so I don't use the repo's version)

**Multiple day Forecast**

And if you are running the five day forecast the days and Hi/Low are done with one call with horizontal spacings in the "template"
So the code would be like this
```

${execi 3600 blah blah to get 5 day names and high/lows --template=xx}
${voffset 5}${font weather:size=45}${execi 3600 python ~/Projects/Weather/Weather.com/conkyForecast.py --location=08628 --startday=0 --endday=4 -n --datatype=WF}$font$color

```
and you'd see:
```

Sun Mon Tue Wed Thu Fri Sat



21/15 23/16 28/20 28/22 25/19
F    F    F    F    F

```
What is needed here is a much larger ${voffset x} something like 45 or so.

When I'm "setting up" I start with 50 and increase or decrease by 10 until it close, then by 5's to get it closer yet and then by 1's to "fine tune" to get:
```
Sun Mon Tue Wed Thu Fri Sat

F    F    F    F    F

21/15 23/16 28/20 28/22 25/19
```
If you use the "weather font" call *before* the five day forecast the voffset value will be a negative value, ${voffset -50}, to move it down.

---

### Post by Bruce M. on 2008-04-26
> **yousillygoose said:**
> I have learned that my problem revolves around :

${alignr}${voffset 5}${offset -70}${font weather:size=45}${color 3f689b}${execi 3600 python ~/scripts/conkyForecast.py --location=08628 --startday=0 -n --datatype=WF}$font$color


the output of the execi doesn't return many spaces so that isnt the problem.

I think the problem may be with the voffset and the offset.  Can anyone test it and tell me what happens.

The negative thing that happens to me is that the bottom of my conky window is expanded a few inches

You do not need the ${offset -70} in that line at all.

Try this: ${alignr 70}

**NOTE:**

If you have a line like this:
```
${alignr}Processes: $running_processes / $processes
```
and your # of running processes is "always" 99 or less no problem, but if they go to 100 or more you'll see conky "blink" as it re-adjusts for the extra character.  Toss a 2 in there and it is always steady as the last character is 2 pixels away from the left boarder:
```
${alignr 2}Processes: $running_processes / $processes
```
By default I never use **${alignr}** I always use **${alignr 2}** as a minimum.

---

### Post by yousillygoose on 2008-04-26
I attached my stuff again with some changes + a screenshot this time.  You can see the bottom of my screenshot I have dragged my mouse to show where the conky window ends.  What else needs to be changed?

---

### Post by Bruce M. on 2008-04-26
> **yousillygoose said:**
> I attached my stuff again with some changes + a screenshot this time.  You can see the bottom of my screenshot I have dragged my mouse to show where the conky window ends.  What else needs to be changed?

I think that space has something to do with the weather fonts and any VOFFSET's you may have used.
Try adding these lines to the bottom of your conky:

```
${voffset 5}${color orange}IP:${alignc}${color white}${addr eth0}${color}
${color lightblue}Down: ${color white}${downspeed eth0}k/s ${alignr 2}${color lightblue}Up: ${color white}${upspeed eth0}k/s ${color}
${color lightblue}Total: ${color white}${totaldown eth0} ${alignr 2}${color lightblue}Total: ${color white}${totalup eth0} ${color}
${color lightblue}Inbound: ${color white}${tcp_portmon 1 32767 count}          ${color lightblue}Outbound: ${color white}${tcp_portmon 32768 61000 count}${alignr 2}${color lightblue}Total: ${color white}${tcp_portmon 1 65535 count} ${color}
${voffset 5}${color orange}Connections: ${color white}${tcp_portmon 32768 61000 count} ${alignr 2} ${color orange}Service/Port ${color}
${voffset 5}${tcp_portmon 32768 61000 rhost 0} ${alignr 2} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr 2} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr 2} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr 2} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr 2} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr 2} ${tcp_portmon 32768 61000 rservice 5}${color}
```
They will set 5 empty lines below your conky for information when you are online downloading something or using Firefox.

You'll have to change "eth0" to what you use, if not "eth0" :)

Now if the first line of that code is way way below your "visible" last line that shows the hi/lows for your 5 Day Forecast (not 3) then on the first line I gave you here increase the ${voffset 5} until that line is just below the hi/lows.

---

### Post by yousillygoose on 2008-04-26
i added those lines to the bottom of my code.  They sit nicely under my Hi/Low's.  Below the code you gave me there is now again empty lines causes by part of my code.  Any more advice?

---

### Post by yousillygoose on 2008-04-26
after playing a lot i feel like voffset only *moves* the visual part of the output.  I think it still takes up the original space where the the date would have been without voffset with blank data.

---

### Post by Bruce M. on 2008-04-28
> **yousillygoose said:**
> i added those lines to the bottom of my code.  They sit nicely under my Hi/Low's.  Below the code you gave me there is now again empty lines causes by part of my code.  Any more advice?

Those empty line are where the URLs go of the first five connections you have when on the net.

---

### Post by yousillygoose on 2008-04-28
no no, the empty lines are the saem as before.  I had all all connctions filled in the conky and blank remove below it still

---

### Post by Bruce M. on 2008-04-28
> **yousillygoose said:**
> no no, the empty lines are the saem as before.  I had all all connctions filled in the conky and blank remove below it still

Have no idea then. I have a blank space like you but it is just for those five lines. :(

---

### Post by Bruce M. on 2008-05-01
Seems like the thread has come to a grinding halt.
So I thought I would post my new "tweaked" weather portion of my conky.

And ask a few questions.

1. Has anyone got the Sunrise Sunset part of the scripts working?
```
sunrise_n = location_n.getElementsByTagName('sunr')[0]
sunrise = self.getText(sunrise_n.childNodes)
sunset_n = location_n.getElementsByTagName('suns')[0]
sunset = self.getText(sunset_n.childNodes)
```
2. The Barometric Pressure part working?
```
bar_n = current_condition_n.getElementsByTagName('bar')[0]
bar_read_n = bar_n.getElementsByTagName('r')[0]
bar_read = self.getText(bar_read_n.childNodes)
bar_desc_n = bar_n.getElementsByTagName('d')[0]
bar_desc = self.getText(bar_desc_n.childNodes)
```
3. Or the Moon Phases?
```
moon_n = current_condition_n.getElementsByTagName('moon')[0]
moon_phase_n = moon_n.getElementsByTagName('t')[0]
moon_phase = self.getText(moon_phase_n.childNodes)
```
Just a thought.

Have a great day
Bruce

---

### Post by kaivalagi on 2008-05-01
> **Bruce M. said:**
> Seems like the thread has come to a grinding halt.
There's been quite a few views of the latest uploaded script, so I'm guessing people are using it, it's just that they're a little shy :cool:

> **Bruce M. said:**
> 
1. Has anyone got the Sunrise Sunset part of the scripts working?
2. The Barometric Pressure part working?
3. Or the Moon Phases?


All do-able as they're in the xml, just need new datatype options, additional class variables to add the data to, and a modified output text function...

My day job is a little hectic at the moment, we have a new release of the in-house workflow app, so time at home has been precious. I have a long weekend coming up, so if I get a chance I'll have a crack at it...no promises though

Anyone else want to give it a try though? All the example code you need is in the script, it needs duplicating and adjusting to suit. Beginner questions welcome, I was one once...Go on Bruce, why don't you give it a shot ;)

P.S. what font are you using for the large temp data?

---

### Post by Bruce M. on 2008-05-02
> **kaivalagi said:**
> Anyone else want to give it a try though? All the example code you need is in the script, it needs duplicating and adjusting to suit. Beginner questions welcome, I was one once...Go on Bruce, why don't you give it a shot ;)

Yea, I'll let my "logical" non-programming brain look at that tomorrow, it might be fun ... specially since you hinted the code is there.

You have to promise not to laugh though.  :lolflag: (hey, I'm allowed)

> **kaivalagi said:**
> P.S. what font are you using for the large temp data?

Zekton - I use it for my entire conky, not just the temps, if I can, I'll attach it.
```
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
```

Have a good day
Bruce

---

### Post by kaivalagi on 2008-05-03
> **Bruce M. said:**
> Yea, I'll let my "logical" non-programming brain look at that tomorrow, it might be fun ... specially since you hinted the code is there.
You have to promise not to laugh though.  :lolflag: (hey, I'm allowed)


PM/email me with any questions and I'll assist. You've already identified that the data is available, next step is to get it into the weatherdata class, once there it can be used with an appropriate datatype flag.

There is one hurdle to overcome, the data is only available for current conditions (not in forecast data). We could just populate with N/A's for the forecast data instead of nothing...

I'm here to help if you need any!

I won't laugh, not publicity anyway :)

Really nice font, I'll have a play...

---

### Post by Bruce M. on 2008-05-03
Just an update folks,

I'm making some headway on the Sunrise & Sunset stuff.

Not there yet and kaivalagi hasn't laughed at me, so I must be doing a little "OK".

I've hit a roadblock, and have a question out for some help.  :)

Will keep you posted.
Have a nice day/evening
Bruce

---

### Post by draxd on 2008-05-05
Could someone add Hourly Forecast to script ?

---

### Post by kaivalagi on 2008-05-05
> **draxd said:**
> Could someone add Hourly Forecast to script ?

There is no such data available from the weather.com xml feed, which is what's currently used in the script.

The only thing that comes close is the high/low temp for 'todays' forecast.

If anyone can tell me where I can find an hourly forecast service, I can take a look...I know of the BBC weather site providing 2-3 hour forecast data but it comes from the met office in the UK I think, so it won't cut it for international users...

As always, I'm open to suggestions for I can be pointed in the right direction...

---

### Post by draxd on 2008-05-05
Hourly Forecast exist on weather.com site , I don`t know about XML feed file tho.
Check : 
```
http://www.weather.com/outlook/travel/businesstraveler/wxdetail/SRXX0006?from=36hr_fcst_business
```
But anyway its realy cool script , I love it , Thanx.

---

### Post by kaivalagi on 2008-05-05
> **draxd said:**
> Hourly Forecast exist on weather.com site , I don`t know about XML feed file tho.
Check : 
```
http://www.weather.com/outlook/travel/businesstraveler/wxdetail/SRXX0006?from=36hr_fcst_business
```
But anyway its realy cool script , I love it , Thanx.

My pleasure :)

---

### Post by yousillygoose on 2008-05-06
uh ohs.  I woke up this morning with a very angry conky.  My error:

fetchData:Unexpected error <type exceptions.IndexError>
Unable to interrogate the current conditions data
fetchData:Unexpect

---

### Post by kaivalagi on 2008-05-06
> **yousillygoose said:**
> uh ohs.  I woke up this morning with a very angry conky.  My error:

fetchData:Unexpected error <type exceptions.IndexError>
Unable to interrogate the current conditions data
fetchData:Unexpect

[SIZE="4"]**[COLOR="Blue"]UPDATE[/COLOR]**[/SIZE]

Any previous script will now break, thanks to a change to the url being necessary after a webservice update.

I've updated the conkyForecast.py so you'll need to download it from the first post again. I had to update the url used to allow to data retrieval to work again.

The weather.com webservice has been updated and now has some improvements / restrictions. [COLOR="Blue"][SIZE="3"]**The forecast data is only available for the next 4 days now**[/SIZE][/COLOR]. So please ensure that you do not use --startday/--endday greater than 4! It will break the script and it tries to fetch something that isn't there.

I will put some error handling at some point to stop the error from occuring, but please bear this in mind if you now have script issues.

Cheers,
Mark

---

### Post by billybag on 2008-05-06
this may have been covered, but when i am not connected to the internet, conky either fills the bottom half of my screen with weather icons or about 10 or so weather icons are displayed with 'no condition available' underneath rather than the 3 day forecast i have it set to display.

---

### Post by kaivalagi on 2008-05-06
> **billybag said:**
> this may have been covered, but when i am not connected to the internet, conky either fills the bottom half of my screen with weather icons or about 10 or so weather icons are displayed with 'no condition available' underneath rather than the 3 day forecast i have it set to display.

There is code to handle the no connection issue:

```
		if self.isConnectionAvailable() == False:
			if os.path.exists(file_path_current):
				RefetchData = False
			else: # no connection, no cache, bang!
				print "No internet connection is available and no cached weather data exists."
```

If you are not connected but there is cached data it should just display previous info. If no connection **_or_** cached data is found you should get the output "No internet connection is available and no cached weather data exists.".

Could it be that what is cached is quite old and not compatible with your current script? Or quite possibly you are calling the script a lot from your conky settings and where you are using the weather font you get lots and lots of weather icons for the error text "No internet connection is available and no cached weather data exists."?

Can you try the following please:

[LIST=1]
[*]Delete the cached data using this command: rm /tmp/conkyForecast*
[*]Connect to the internet then run conky
[*]Close your internet connection
[*]restart conky
[/LIST]

Also, make sure you have updated the script with the very recently updated script, the previous one will not work anymore! See previous post

---

### Post by TB2 on 2008-05-06
Thanks for the update

---

### Post by yousillygoose on 2008-05-06
I have a request for you.  When I'm not connected the weather font freaks out (like you said above).  Is there any way to do like, If connected to the internet use the font specified, if not connected use a normal font.  Thanks

---

### Post by billybag on 2008-05-06
well i dont have a tmp/conkyforcast folder. so perhaps that is the problem.

---

### Post by billybag on 2008-05-06
nevermind. creating that folder just makes the problem occur even when i am conntect

---

### Post by kaivalagi on 2008-05-07
> **billybag said:**
> nevermind. creating that folder just makes the problem occur even when i am conntect

It is not a folder, there are 3 cache files in the /tmp folder starting with the name conkyForecast...

---

### Post by kaivalagi on 2008-05-07
> **yousillygoose said:**
> I have a request for you.  When I'm not connected the weather font freaks out (like you said above).  Is there any way to do like, If connected to the internet use the font specified, if not connected use a normal font.  Thanks

Unfortunately the weather font is a setting in conky and not in the script, there is no way round this other than returning nothing.

I could maybe only return the error when the --verbose option is used, that way when you get stuck run with --verbose and no weather font settings in the conky config to see what's going on...

---

### Post by dccrens on 2008-05-07
Well everything has been working very well until yesterday. I started receiving errors that say:
Unexpected error: < type 'exceptions.IndexError'>
Unable to interrogate the current conditions data

This happens for all of the calls I am using, Temp, Precip, etc.

Is anyone else having this problem?

If I run one of the calls from the command line I get:

python ~/Scripts/conkyForecast.py --location=USVA0427 -i --refetch --datatype=LT

Unexpected error: <type 'exceptions.IndexError'>
Unable to interrogate the current conditions data
Unexpected error: <type 'exceptions.IndexError'>
Unable to interrogate the forecast data
Traceback (most recent call last):
File "/home/dccrens/Scripts/conkyForecast.py", line 855, in <module>
weather.output_data()
File "/home/dccrens/Scripts/conkyForecast.py", line 646, in output_data
string = self.current_conditions[0].low
IndexError: list index out of range

---

### Post by dccrens on 2008-05-07
Nevermind! D/L'ing the fixed script worked. I should learn to read back a few pages...

---

### Post by Bruce M. on 2008-05-07
> **dccrens said:**
> Nevermind! D/L'ing the fixed script worked. I should learn to read back a few pages...

Hi Dave, I just got notified by email of a new post here --- yours.

Glad to see you fixed it with the download, reading is good at times. :)

Have a nice day.
Bruce

---

### Post by kaivalagi on 2008-05-10
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Hi All,

I have just updated the script and details of this in the first post. The following has been done:

[LIST]
[*]Consolidated current condition and forecast data fetch into one call
[*]Added Sunrise and sunset to datatypes, these are specific to both current conditions and forecast data
[*]Added moon phase, barometer reading and barometer description to datatypes, these are only specific to current conditions and so are N/A in forecast output
[*]Added unit conversions for barometer from mb to inches (imperial)
[*]Updated Spanish condition text - Thanks Bruce M
[/LIST]

I'll be taking a break from developing this script for the next couple of weeks, so don't expect any more updates for a while (unless it stops working altogether!). The weather has just turned nice in the UK and I want to make the most of it :) I will still be checking on this thread though ;)

BTW, I know there have been a lot of downloads of the various incarnations of this python script, so please, to help others, post your working conky config files/templates etc with a screenshot

Enjoy!

---

### Post by Bruce M. on 2008-05-10
Hi Folks,

WoW! One "execi" call gets everything, great news for us low powered CPU users.

Here is an earlier shot of my conky with todays weather and a two day forecast. All formatted nicely within my conky display.

[CENTER][[IMG]http://img216.imageshack.us/img216/1040/nooutputpc6.th.jpg[/IMG]](http://img216.imageshack.us/my.php?image=nooutputpc6.jpg)[/CENTER]

It took 22 execi calls to do that. Just a little intensive. But I liked it as it gave me a bit of a forecast.

Well, with this new PY script I have send out a HUGE

[CENTER][SIZE="7"]thank you kaivalagi[/SIZE]
for creating a one call gets all PY script.[/CENTER]

Also, while I'm getting credit for the Spanish part of the script, recently I have been helped with some of the translations. So I would like to **publicly thank jjgomera** for his/her help. It's been nice chatting with you, I hope we continue, there is more to be done.

Now to continue. First with a screen shot. I have two conky's running again, and this morning I added "Today" to the conky on the left just to show you all the information that this PY file gets with just ONE "execi" call.

[CENTER][[IMG]http://img293.imageshack.us/img293/6750/latestgi1.th.jpg[/IMG]](http://img293.imageshack.us/my.php?image=latestgi1.jpg)[/CENTER]

Left conky config file: conkyforecast
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
draw_shades no
draw_outline yes  # amplifies text if yes
draw_borders no
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment bottom_left  # top_right, top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
no_buffers yes  # Subtract file system buffers from used memory?
draw_outline yes
draw_shades yes  # shadecolor black
default_outline_color black
default_shade_color black
# 40
TEXT
${color cyan}${hr 1}$color
${color lightblue}${font zekton:size=9}${execi 3600 python /home/bruloo/scripts/conkyForecast.py --location=ARBA0009 --template=/home/bruloo/scripts/conkyForecast.template}$font$color
```
The conkyforecast.template:
```
Desde: {--datatype=CN}
{--datatype=DW}:  {--datatype=CC}
{--datatype=HT} / {--datatype=LT}   Viento del {--datatype=WD}  a  {--datatype=WS}
Humedad: {--datatype=HM}          Precipitacion: {--datatype=PC}
Presion: {--datatype=BR} - {--datatype=BD}
Salida del Sol: {--datatype=SR}   Ocaso: {--datatype=SS}
Luna:  {--datatype=MP}
---------------
{--datatype=DW --startday=1}:  {--datatype=CC --startday=1}
{--datatype=HT --startday=1} / {--datatype=LT --startday=1}   Viento del {--datatype=WD --startday=1}  a  {--datatype=WS --startday=1}
Humedad: {--datatype=HM --startday=1}          Precipitacion: {--datatype=PC --startday=1}
Salida del Sol: {--datatype=SR --startday=1}   Ocaso: {--datatype=SS --startday=1}
---------------
{--datatype=DW --startday=2}:  {--datatype=CC --startday=2}
{--datatype=HT --startday=2} / {--datatype=LT --startday=2}   Viento del {--datatype=WD --startday=2}  a  {--datatype=WS --startday=2}
Humedad: {--datatype=HM --startday=2}          Precipitacion: {--datatype=PC --startday=2}
Salida del Sol: {--datatype=SR --startday=2}   Ocaso: {--datatype=SS --startday=2}
---------------
{--datatype=DW --startday=3}:  {--datatype=CC --startday=3}
{--datatype=HT --startday=3} / {--datatype=LT --startday=3}   Viento del {--datatype=WD --startday=3}  a  {--datatype=WS --startday=3}
Humedad: {--datatype=HM --startday=3}          Precipitacion: {--datatype=PC --startday=3}
Salida del Sol: {--datatype=SR --startday=3}   Ocaso: {--datatype=SS --startday=3}
---------------
{--datatype=DW --startday=4}:  {--datatype=CC --startday=4}
{--datatype=HT --startday=4} / {--datatype=LT --startday=4}   Viento del {--datatype=WD --startday=4}  a  {--datatype=WS --startday=4}
Humedad: {--datatype=HM --startday=4}          Precipitacion: {--datatype=PC --startday=4}
Salida del Sol: {--datatype=SR --startday=4}   Ocaso: {--datatype=SS --startday=4}
```
And my: conkymain
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
draw_shades no
draw_outline yes  # amplifies text if yes
draw_borders no
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment top_right  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
no_buffers yes  # Subtract file system buffers from used memory?
draw_outline yes
draw_shades yes  # shadecolor black
default_outline_color black
default_shade_color black

TEXT
${font Zekton:size=11}${color lightblue}${alignc}*** ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color lightblue}***$color$font
${font Zekton:size=11}${alignc}${Color orange}** ${color lightblue}Canada ${color orange}**$color$font
${color lightblue}Winnipeg${color lightblue}: ${color white}${tztime Canada/Central %H:%M}$color${alignr 2}${color lightblue}London${color lightblue}: ${color white}${tztime Canada/Eastern %H:%M}$color
${color lightblue}Winnipeg${color lightblue}: ${color white}${tztime Canada/Central %H:%M}$color${alignr 2}${color lightblue}London${color lightblue}: ${color white}${tztime Canada/Eastern %H:%M}$color
${color cyan}${hr 1}$color
${alignc}${color lightblue}--> ${color orange}bruloo @ bruloo ${color lightblue}<--$color
${font Zekton:size=20}${color white}${alignc}${time %H:%M}$color$font
${font Zekton:size=12}${color lightblue}${alignc}${time %A, %d %b. %Y}$color$font
${color yellow}UpTime:${alignr 2}$uptime$color
${color cyan}${hr 1}$color
${voffset 5}${color orange}CPU:${alignc}$color$running_processes ${color lightblue}/ $color$processes${alignr 2}${color orange}${cpubar cpu0 14,100}$color
${color lightblue}${voffset -16}${alignr 5}$cpu%
${voffset 2}${color lightblue}Load Avg (${color yellow}Min${color lightblue}):${alignr 2}${color yellow}1: ${color white}${loadavg 1}   ${color yellow}5: ${color white}${loadavg 2}   ${color yellow}15: ${color white}${loadavg 3} ${color orange}$color
${voffset 5}${color orange}RAM:$color $mem ${color orange}/ $color$memmax${alignr 2}${color orange}${membar 14,100}
${color lightblue}${voffset -16}${alignr 5}$memperc%
${voffset 2}${color lightblue}Buffered: ${color white}${buffers}$color${alignr 2}${color lightblue}Cached:${color white} ${cached}$color
${voffset 5}${color orange}SWAP: $color$swap ${color orange}/ $color${swapmax}${alignr 2}${color orange}${swapbar 14,100}$color
${color lightblue}${voffset -16}${alignr 5}$swapperc%
${color cyan}${hr 1}$color
${voffset 5}${color orange}HD Info${color lightblue} -$color Free${color lightblue} - Used - ${color orange} Total
${voffset 5}${color lightblue}Root: $color${fs_free_perc /} %${alignr 2}${fs_free /} ${color orange}/ ${color lightblue}${fs_used /}$color de ${color orange}${fs_size /}$color
${color lightblue}Home: $color${fs_free_perc /home/bruloo} %${alignr 2}${fs_free /home/bruloo} ${color orange}/ ${color lightblue}${fs_used /home/bruloo}$color de ${color orange}${fs_size /home/bruloo}$color
${color lightblue}BruLoo: $color${fs_free_perc /media/BruLoo} %${alignr 2}${fs_free /media/BruLoo} ${color orange}/ ${color lightblue}${fs_used /media/BruLoo}${color white} de ${color orange}${fs_size /media/BruLoo}$color
${color lightblue}40G: $color${fs_free_perc /media/sdb1} %${alignr 2}${fs_free /media/sdb1} ${color orange}/ ${color lightblue}${fs_used /media/sdb1}$color de ${color orange}${fs_size /media/sdb1}$color
${color cyan}${hr 1} $color
${color lightblue}Desde:$color Buenos Aires, Argentina
${color lightblue}Lat: ${color orange}34°35'S          ${color lightblue}Long: ${color orange}58°21'W            ${color lightblue}Alt: ${color orange}25 m$color
${voffset 5}${color orange}${font Zekton:size=12}hoy:$font ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC}$color
${color lightblue}Salida del Sol: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=SR}${alignr -2}${color lightblue}Ocaso: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=SS}$color
${alignc}${color lightblue}Luna: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=MP}$color
${voffset 5}${alignr 2}${color lightblue}Viento: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS} ${color lightblue}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=WD}$color
${alignr 2}${color lightblue}Humedad: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM}
${alignr 2}${color lightblue}Precipitación: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC}$color
${voffset -45}${font Zekton:size=25}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT}$font
${voffset 5}${alignc}${color lightblue}Presión: ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=BR} - ${color yellow}${execi 3600 python ~/scripts/conkyForecast.py --location=ARBA0009 --datatype=BD}$color
${voffset -0}${color cyan}${hr 1}$color
${voffset 5}${color orange}IP:${alignc}$color${addr eth0}
${color lightblue}Down: $color${downspeed eth0}k/s ${alignr 2}${color lightblue}Up: $color${upspeed eth0}k/s
${color lightblue}Total: $color${totaldown eth0} ${alignr 2}${color lightblue}Total: $color${totalup eth0} 
${color lightblue}Inbound: $color${tcp_portmon 1 32767 count}          ${color lightblue}Outbound: $color${tcp_portmon 32768 61000 count}${alignr 2}${color lightblue}Total: $color${tcp_portmon 1 65535 count} 
${voffset 5}${color orange}Connections: $color${tcp_portmon 32768 61000 count} ${alignr 2} ${color orange}Service/Port $color
${voffset 5}${tcp_portmon 32768 61000 rhost 0} ${alignr 2} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr 2} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr 2} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr 2} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr 2} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr 2} ${tcp_portmon 32768 61000 rservice 5}$color
```
I'll be stripping out the "Today" stuff on the left and leaving it as a simple 4 Day Forecast because I do like the complete format for Today in my conkymain.

One last thing. If you want a "DEFAULT" Spanish conky (what's working to date) change this part of your conkyForecast.py file:
```
	def __init__(self,options):

		self.options = options
		
		if self.options.locale == None:
			try:
				#self.locale = locale.getdefaultlocale()[0][0:2]
				self.locale = "es"
			except:
				print "locale not set"
		else:
			#self.locale = self.options.locale
			self.locale = "es"
```
If I can help anyone, just ask.
Have a great day with great weather.
Bruce

---

### Post by benpaka on 2008-05-10
> **kaivalagi said:**
> **[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Hi All,

I have just updated the script and details of this in the first post. The following has been done:

[LIST]
[*]Consolidated current condition and forecast data fetch into one call
[*]Added Sunrise and sunset to datatypes, these are specific to both current conditions and forecast data
[*]Added moon phase, barometer reading and barometer description to datatypes, these are only specific to current conditions and so are N/A in forecast output
[*]Added unit conversions for barometer from mb to inches (imperial)
[*]Updated Spanish condition text - Thanks Bruce M
[/LIST]

I'll be taking a break from developing this script for the next couple of weeks, so don't expect any more updates for a while (unless it stops working altogether!). The weather has just turned nice in the UK and I want to make the most of it :) I will still be checking on this thread though ;)

BTW, I know there have been a lot of downloads of the various incarnations of this python script, so please, to help others, post your working conky config files/templates etc with a screenshot

Enjoy!

Hy, This script is terrible ... The best one I think !!
I just want to ask if we can have the meteo for the next 6 hours...
Because it is cool to have actual and tonight but it should changes when we are the evening! 


Otherwise i'v made a small contribution with french translation:

```

	conditions_text_fr = {
        "0": _(u"Tornade"),
        "1": _(u"Tempête Tropicale"),
        "2": _(u"Ouragan"),
        "3": _(u"Orages Violents"),
        "4": _(u"Orageux"),
        "5": _(u"Pluie et Neige"),
        "6": _(u"Pluie et Neige Mouillée"),
        "7": _(u"Variable avec averses"),
        "8": _(u"Bruine Givrante"),
        "9": _(u"Bruine"),
        "10": _(u"Pluie Glacante"),
        "11": _(u"Averses"),
        "12": _(u"Averses"),
        "13": _(u"Légère Neige"),
        "14": _(u"Forte Neige"),
        "15": _(u"Tempête de Neige"),
        "16": _(u"Neige"),
        "17": _(u"Grêle"),
        "18": _(u"Pluie/Neige"),
        "19": _(u"Nuage de poussière"),
        "20": _(u"Brouillard"),
        "21": _(u"Brume"),
        "22": _(u"Fumée"),
        "23": _(u"Tres Venteux"),
        "24": _(u"Venteux"),
        "25": _(u"Froid"),
        "26": _(u"Nuageux"),
        "27": _(u"Tres Nuageux"),
        "28": _(u"Tres Nuageux"),
        "29": _(u"Nuages Disséminés"),
        "30": _(u"Nuages Disséminés"),
        "31": _(u"Beau"),
        "32": _(u"Beau"),
        "33": _(u"Belles éclaircies"),
        "34": _(u"Belles éclaircies"),
        "35": _(u"Pluie avec Grêle"),
        "36": _(u"Chaleur"),
        "37": _(u"Orages Isolés"),
        "38": _(u"Orages Localisés"),
        "39": _(u"Orages Localisés"),
        "40": _(u"Averses Localisées"),
        "41": _(u"Neige Lourde"),
        "42": _(u"Tempête de Neige Localisées"),
        "43": _(u"Neige Lourde"),
        "44": _(u"Nuages Disséminés"),
        "45": _(u"Orages"),
        "46": _(u"Tempête de Neige"),
        "47": _(u"Orages Isolés"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
	}

	day_of_week_fr = {
		"Today": _(u"Aujourd'hui"),
		"Monday": _(u"Lundi"),
		"Tuesday": _(u"Mardi"),
		"Wednesday": _(u"Mercredi"),
		"Thursday": _(u"Jeudi"),
		"Friday": _(u"Vendredi"),
		"Saturday": _(u"Samedi"),
		"Sunday": _(u"Dimanche")
	}

	day_of_week_short_fr = {
		"Today": _(u"Auj"),
		"Monday": _(u"Lun"),
		"Tuesday": _(u"Mar"),
		"Wednesday": _(u"Mer"),
		"Thursday": _(u"Jeu"),
		"Friday": _(u"Ven"),
		"Saturday": _(u"Sam"),
		"Sunday": _(u"Dim")
	}

```

---

### Post by benpaka on 2008-05-10
Here you have my desktop : 

[[IMG]http://elraton.free.fr/divers/misc/buro-conky-thumbs.png[/IMG]]("http://elraton.free.fr/divers/misc/buro-conky.png")

And in the dual screen mode :[Dual screen desktop]("http://elraton.free.fr/divers/misc/buro-full.png")

My .conkyrc
> 
#How to run
background yes
update_interval 2
cpu_avg_samples 2
net_avg_samples 2
text_buffer_size 256


#Font
use_xft yes
xftfont Bitstream Vera Sans:size=7
xftalpha 0.8
color0 aaaaaa
color1 88bbff

#Windows position
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager


#Boders
border_margin 1
border_width 1
#draw_border yes
draw_graph_borders yes
stippled_borders no


# Shade and outline
draw_shades no
draw_outline no
default_color white
default_shade_color grey


#Position
alignment bottom_right
minimum_size 200
maximum_width 200
gap_y 20
gap_x 20

double_buffer yes
use_spacer none
no_buffers yes

TEXT
${color1}System informations  ${color} $hr
$nodename  ${alignr} Uptime:${color} $uptime 
${color1}CPU Usage:$color ${alignr}  ${cpu cpu0}%  |  ${acpitemp}°C  |  ${freq_g}GHz
${color1}RAM Usage:$color $memperc% ${alignr}  ${color1}Swap Usage:$color $swapperc%
$alignc ---------
${color1}File systems:$color 
/      ${alignr} ${fs_used /} / ${fs_size /}   (${fs_free_perc /}% free)
home   ${alignr} ${fs_used /home/neub} / ${fs_size /home/neub}   (${fs_free_perc /home/neub}% free)
${if_mounted /media/USB_250}U250 ${alignr} ${fs_used /media/USB_250} / ${fs_size /media/USB_250}  (${fs_free_perc /media/USB_250}% free)
${endif} $alignc ---------
${color1}Wifi$color  ${alignr} ${downspeed eth1} kb/s DOWN   /   ${upspeed eth1} kb/s UP
IPs: ${alignr}  ${addr eth1}  /  ${execi 1000 wget -O - [http://ip.tupeux.com](http://ip.tupeux.com) | tail}
$alignc ---------
${color1}Processus : ${alignr 20}PID ${alignr 10}%CPU ${alignr} %MEM$color
${top name 1} ${alignr 20}${top pid 1} ${alignr 10}${top cpu 1} ${alignr 0} ${top mem 1}
${top name 2} ${alignr 20}${top pid 2} ${alignr 10}${top cpu 2} ${alignr 0} ${top mem 2}
${top name 3} ${alignr 20}${top pid 3} ${alignr 10}${top cpu 3} ${alignr 0} ${top mem 3}
$color$hr
 

${color1}Weather forecast${color} $hr
${execi 600 python /home/neub/.conkyconf/scripts/conkyForecast.py --locale=fr --location=SPXX0200 --template=/home/neub/.conkyconf/scripts/conkyActual.template}
${font weather:size=27}${color 3f689b}${execi 600 python /home/neub/.conkyconf/scripts/conkyForecast.py --location=SPXX0200 --startday=1 --endday=3 --datatype=WF --spaces=2}$font$color
${execi 600 python /home/neub/.conkyconf/scripts/conkyForecast.py --locale=fr --location=SPXX0200 --template=/home/neub/.conkyconf/scripts/conky3Days.template}
$color$hr


${color1}Todo List  ${color} $hr
${execi 600 cat ~/.TODO}
$hr



And the two template that i use:

**conkyActual.template**
> 
Ville:   {--datatype=CN }
Current: {--locale=es --datatype=CC --startday=0 }
Tonight: {--locale=es --datatype=CC --night --startday=0}
Min/Max: {--datatype=LT --startday=0}/{--datatype=HT}   -   Precipitation:{--datatype=PC --startday=0}


**conky3Days.template**
> 
  {--datatype=DW --startday=1 --shortweekday}                     {--datatype=DW --startday=2 --shortweekday}                    {--datatype=DW --startday=3 --shortweekday}
{--datatype=LT --startday=1 --hideunits}/{--datatype=HT --startday=1 }              {--datatype=LT --startday=2 --hideunits}/{--datatype=HT --startday=2}             {--datatype=LT --startday=3 --hideunits}/{--datatype=HT --startday=3}
  {--datatype=PC --startday=1}                    {--datatype=PC --startday=2}                    {--datatype=PC --startday=3 }



Thanks for your good script...

---

### Post by kaivalagi on 2008-05-10
> **benpaka said:**
> Hy, This script is terrible ... The best one I think !!
I just want to ask if we can have the meteo for the next 6 hours...
Because it is cool to have actual and tonight but it should changes when we are the evening!

I am guessing you mean terrific and not terrible :)

I know what you mean, not an easy thing to sort out. It will require a mix of current and forecast data. Before 2pm, the night data is sufficient for the upcoming hours, when you get into the evening then the 'next' weather should be from the following morning, which at that time is startday==1 data...see what I mean?

Once I've had some time off and have recharged my python scripting batteries, I'll give it some more thought...

> **benpaka said:**
> 
Otherwise i'v made a small contribution with french translation:

That's great, thank you, the more languages the better. This will be the next thing I sort out and plug into the script, there will be a --locate=fr option for it etc.

If we get a few more languages on board I will then start thinking about creating separate class files to hold the language data, which users can copy into the folder if they are needed...

Any takers for Fijian text? I'll ask my wife to do some translations :)

Have conkying!

P.S. Good to see you are using the template feature, I'm glad it has found good use!

---

### Post by dccrens on 2008-05-11
Many thanks to kaivalagi for his hard work on this. I haven't had a chance to upgrade to the templates version yet but on my system (X6800 at 3600Ghx with 8800GTX) the previous version is great. Execi calls are ok... 

Here are a couple of screenshots:

---

### Post by jjgomera on 2008-05-12
First of all, Thank you very much to **kaivalagi** to do this script, i like to thank to **Bruce M.** too to translate the spanish weather current conditions =D>

Here is my conkyweather:

```
# maintain spacing between certain elements
use_spacer right

# set to yes if you want tormo to be forked in the background
background no

use_xft yes

# Xft font when Xft is enabled
#xftfont Vera-8
#xftfont Andale Mono-8
#xftfont Clean-8
#xftfont cubicfive10:pixelsize=8
xftfont Sans-Serif:size=9:pixelsize=11
#xftfont swf!t_v02:pixelsize=11

# Text alpha when using Xft
xftalpha 1
#mail_spool $MAIL

# Update interval in seconds
update_interval 2.0

# Create own window instead of using desktop (required in nautilus) normal desktop or override
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

#own_window_hints below

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 100 5
maximum_width 500

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no # amplifies text

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders 3

# border margins
border_margin 5

# border widt5
border_width 6

# Default colors and also border colors,
default_color gold
default_shade_color black
default_outline_color DarkGrey


# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 0
gap_y -35

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no


TEXT
${color white}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=CN}
${voffset -5}${color}${hr 1}$color
${font Weather:size=36}${color white}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=WF}${font}${color}
${voffset -40}${offset 60}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=HT}
${offset 60}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=BR}
${offset 60}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=WS}km/h ${font Wingdings:size=10}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=WD}$font
${voffset -47}${offset 150}           ${color white}${font Weather:size=24}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=WF --startday=1 --endday=4}${font}${color}
   ${offset 145}${color white}${font Weather:size=16}i${font}:   ${voffset -3}${color gold}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=PC --startday=1 --endday=4 --spaces=7}
   ${offset 150}${color white}${font Weather:size=16}v${font}:   ${voffset -3}${color gold}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=WS --startday=1 --endday=4 --spaces=3}
   ${offset 150}${color white}${font Weather:size=16}z${font}:    ${voffset -3}${color gold}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=HT --startday=1 --endday=4 --spaces=6}
${voffset -25}${color white}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=CC}
Humedad: ${color}${execi 3600 python ~/configuracion/conkyForecast.py --location=SPXX0098 --datatype=HM}
${voffset -5}${color #ffd700}${hr 1}$color
```I find more intuitive use arrows to wind directions, so i have made a tweak in a section of conkyforecast.py, i change the N, NE... indications for:

```
    def getBearingText(self,bearing):
        bearing = float(bearing)
        if bearing < 11.25:
            return u"Í"
        if bearing < 33.75:
            return u"Ï"
        if bearing < 56.25:
            return u"Ï"
        if bearing < 78.75:
            return u"Ï"
        if bearing < 101.25:
            return u"Á"
        if bearing < 123.75:
            return u"Î"
        if bearing < 146.25:
            return u"Î"
        if bearing < 168.75:
            return u"Î"
        if bearing < 191.25:
            return u"È"
        if bearing < 213.75:
            return u"Ï"
        if bearing < 236.25:
            return u"Ï"
        if bearing < 258.75:
            return u"Ï"
        if bearing < 281.25:
            return u"Ë"
        if bearing < 303.75:
            return u"Ó"
        if bearing < 326.25:
            return u"Ó"
        if bearing < 348.75:
            return u"Ó"
```So i can use Wingdings font to draw arrows, really i didn't find any free font with arrows :(
But this tweak only work with current wind, but no for 'n' days forecast, and i dont know programing

[QUOTE=Bruce M.]It's been nice chatting with you, I hope we continue, there is more to be done.[/QUOTE]I hope it too :)

---

### Post by Bruce M. on 2008-05-12
> **jjgomera said:**
> First of all, Thank you very much to **kaivalagi** to do this script, i like to thank to **Bruce M.** too to translate the spanish weather current conditions =D>

Hey, you helped, I just started it.  :)

> **jjgomera said:**
> I find more intuitive use arrows to wind directions, so i have made a tweak in a section of conkyforecast.py, i change the N, NE... indications for:

   {snip}

So i can use Wingdings font to draw arrows, really i didn't find any free font with arrows :(
But this tweak only work with current wind, but no for 'n' days forecast, and i dont know programing

I hope it too :)

Nice idea, I'm going to look for a free "arrow" font.  :)

I know it only works for "today" and not the forecast, I'm just beginning to learn python and I have been testing it for a couple of days now trying to get that Spanish working for wind direction. The only change is for West; Oeste the rest are the same = N E S y O.  :)

---

### Post by kaivalagi on 2008-05-12
> **Bruce M. said:**
> Hey, you helped, I just started it.  :)



Nice idea, I'm going to look for a free "arrow" font.  :)

I know it only works for "today" and not the forecast, I'm just beginning to learn python and I have been testing it for a couple of days now trying to get that Spanish working for wind direction. The only change is for West; Oeste the rest are the same = N E S y O.  :)

On the bearing arrows front, I think it best to do the following:
1) leave in place the current getBearingText function to allow all bearings data to be in the base form of NSEW whether it is current or forecast based.
2) Have a new datatype e.g. say --datatype==BF (bearing font) which notifies the script to convert the "base" bearing into the correct character, in a similar way to the --datatype==WF option for weather fonts.

Also would this mean we ignore outputting locale specific NSEW e.g. NSEO for es? If you still need that output too then for different locates such as "es" we should have another list equivalent to the conditions code to text list, which again is based on the NSEW being the input.

What would the French equivalent NSEW be? NSEW or something else?

I hope that makes sense...bottom line is we try to keep a base set of data which we convert from, so we know where we stand.

I can get started on this at the end of the week, maybe sooner :) If someone could come up with the lists for both arrow characters and Spanish/French in the meantime I'll have something easy to plug into.

An example of the lists would be, replace ? with correct char for arrows, not sure whether I got the "es" one right...:

```
	bearing_arrow_font = {
	    "N": _(u"?"),
	    "NNE": _(u"?"),
	    "NE": _(u"?"),
	    "ENE": _(u"?"),
	    "E": _(u"?"),
	    "ESE": _(u"?"),
	    "SE": _(u"?"),
	    "SSE": _(u"?"),
	    "S": _(u"?"),
	    "SSW": _(u"?"),
	    "SW": _(u"?"),
	    "WSW": _(u"?"),
	    "W": _(u"?"),
	    "WNW": _(u"?"),
	    "NW": _(u"?"),
	    "NNW": _(u"?")
	}

	bearing_text_es = {
	    "N": _(u"N"),
	    "NNE": _(u"NNE"),
	    "NE": _(u"NE"),
	    "ENE": _(u"ENE"),
	    "E": _(u"E"),
	    "ESE": _(u"ESE"),
	    "SE": _(u"SE"),
	    "SSE": _(u"SSE"),
	    "S": _(u"S"),
	    "SSW": _(u"SSO"),
	    "SW": _(u"SO"),
	    "WSW": _(u"WOW"),
	    "W": _(u"W"),
	    "WNW": _(u"ONO"),
	    "NW": _(u"NO"),
	    "NNW": _(u"NNO")
	}


```

[COLOR="Blue"]Edit: Ideally we need a new font for the arrows so we get the exact direction right, rather than just up, down, left, right...which I think Bruce was hinting at...:)

Edit of edit: I've sorted output of a BF datatype and locale based WD output too, I just need those lists! Can't help myself...emailed yourself and jjgomera a copy :)[/COLOR]

---

### Post by TB2 on 2008-05-12
FYI:

I get some errors when starting conky, that didn't show up before. I didn't change anything. I'm with the latest version. Everything seems to work right, so I don't really care, but this is what I get when starting conky (and everytime the weather part refreshes:

```
[shapeshifter@Tachychineta | 17:16:21] $ conky &
[1] 6526
[shapeshifter@Tachychineta | 17:16:24] $ Conky: desktop window (140000f) is subwindow of root window (6a)
Conky: drawing to desktop window
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1037, in <module>
    weather.outputData()
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1010, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 651, in getOutputText
    output = u""+output.strip(u" ") # lose leading/trailing spaces
AttributeError: 'NoneType' object has no attribute 'strip'
Traceback (most recent call last):
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1037, in <module>
    weather.outputData()
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1010, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 651, in getOutputText
    output = u""+output.strip(u" ") # lose leading/trailing spaces
AttributeError: 'NoneType' object has no attribute 'strip'
```

---

### Post by kaivalagi on 2008-05-12
> **TB2 said:**
> FYI:

I get some errors when starting conky, that didn't show up before. I didn't change anything. I'm with the latest version. Everything seems to work right, so I don't really care, but this is what I get when starting conky (and everytime the weather part refreshes:

```
[shapeshifter@Tachychineta | 17:16:21] $ conky &
[1] 6526
[shapeshifter@Tachychineta | 17:16:24] $ Conky: desktop window (140000f) is subwindow of root window (6a)
Conky: drawing to desktop window
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1037, in <module>
    weather.outputData()
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1010, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 651, in getOutputText
    output = u""+output.strip(u" ") # lose leading/trailing spaces
AttributeError: 'NoneType' object has no attribute 'strip'
Traceback (most recent call last):
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1037, in <module>
    weather.outputData()
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 1010, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/shapeshifter/Scripts/General/conkyForecast.py", line 651, in getOutputText
    output = u""+output.strip(u" ") # lose leading/trailing spaces
AttributeError: 'NoneType' object has no attribute 'strip'
```

Can you try deleting the cache files from your /tmp/ folder with the following and then run it again:

```
rm /tmp/conkyForecast*
```

It looks like the script is not finding the text data it should...whether than be from the cache or a new web call, I'm not sure...

Let me know what happens after you've done the above

[COLOR="Blue"]Edit: If it doesn't fix the issue post your conky config and I'll step through the code to see what the problem is...

Edit of edit: You must be missing 2 conkyForecast execi outputs somewhere in your conky display...[/COLOR]

Cheers

P.S. It's always a good idea to delete the cache after a script is downloaded, to make sure the data is retrieved afresh

---

### Post by jjgomera on 2008-05-12
> **kaivalagi said:**
>  
Also would this mean we ignore outputting locale specific NSEW e.g. NSEO for es? If you still need that output too then for different locates such as "es" we should have another list equivalent to the conditions code to text list, which again is based on the NSEW being the input.

What would the French equivalent NSEW be? NSEW or something else?


Really I think NSEW is a international nomenclature, in spanish it use W so than O, but if you want..:)


> **kaivalagi said:**
> 
[COLOR=Blue]Edit: Ideally we need a new font for the arrows so we get the exact direction right, rather than just up, down, left, right...which I think Bruce was hinting at...:)
[/COLOR]
It's easier make a new font than find any free font so, see the attachment, if anybody want to improve it, its free

And this the correspondence:

   ```
bearing_arrow_font = {
        "N": _(u"N"),
        "NNE": _(u"M"),
        "NE": _(u"I"),
        "ENE": _(u"F"),
        "E": _(u"E"),
        "ESE": _(u"D"),
        "SE": _(u"J"),
        "SSE": _(u"R"),
        "S": _(u"S"),
        "SSW": _(u"T"),
        "SW": _(u"K"),
        "WSW": _(u"V"),
        "W": _(u"W"),
        "WNW": _(u"X"),
        "NW": _(u"H"),
        "NNW": _(u"O")
    }

```

---

### Post by Bruce M. on 2008-05-12
> **kaivalagi said:**
> On the bearing arrows front, I think it best to do the following:
1) leave in place the current getBearingText function to allow all bearings data to be in the base form of NSEW whether it is current or forecast based.
2) Have a new datatype e.g. say --datatype==BF (bearing font) which notifies the script to convert the "base" bearing into the correct character, in a similar way to the --datatype==WF option for weather fonts.

Also would this mean we ignore outputting locale specific NSEW e.g. NSEO for es? If you still need that output too then for different locates such as "es" we should have another list equivalent to the conditions code to text list, which again is based on the NSEW being the input.

I wouldn't ignore them at all, there are bound to be people that will not want the arrows. And {--datatype=WF} doesn't work in the "Templates", I tried it and got an [SIZE="6"]a[/SIZE] for sunny.  :)


Also, they will have to be "small" as a North or South arrow will be larger then the text size. But saying that I saw your samples, I like those, only I'd shorten the "stem".  :)

> **kaivalagi said:**
> What would the French equivalent NSEW be? NSEW or something else?

French is easy, it's the same as Spanish: NESO (Nord Sud Est Ouest)

> **kaivalagi said:**
> I hope that makes sense...bottom line is we try to keep a base set of data which we convert from, so we know where we stand.

I can get started on this at the end of the week, maybe sooner :) If someone could come up with the lists for both arrow characters and Spanish/French in the meantime I'll have something easy to plug into.

An example of the lists would be, replace ? with correct char for arrows, not sure whether I got the "es" one right...:

```
	bearing_arrow_font = {
	    "N": _(u"?"),
	    "NNE": _(u"?"),
	    "NE": _(u"?"),
	    "ENE": _(u"?"),
	    "E": _(u"?"),
	    "ESE": _(u"?"),
	    "SE": _(u"?"),
	    "SSE": _(u"?"),
	    "S": _(u"?"),
	    "SSW": _(u"?"),
	    "SW": _(u"?"),
	    "WSW": _(u"?"),
	    "W": _(u"?"),
	    "WNW": _(u"?"),
	    "NW": _(u"?"),
	    "NNW": _(u"?")
	}

	bearing_text_es = {
	    "N": _(u"N"),
	    "NNE": _(u"NNE"),
	    "NE": _(u"NE"),
	    "ENE": _(u"ENE"),
	    "E": _(u"E"),
	    "ESE": _(u"ESE"),
	    "SE": _(u"SE"),
	    "SSE": _(u"SSE"),
	    "S": _(u"S"),
	    "SSW": _(u"SSO"),
	    "SW": _(u"SO"),
	    "WSW": _(u"WOW"),
	    "W": _(u"W"),
	    "WNW": _(u"ONO"),
	    "NW": _(u"NO"),
	    "NNW": _(u"NNO")
	}


```[

Only one mistake: West:
```
"W": _(u"O"),
```
> **kaivalagi said:**
> [COLOR="Blue"]Edit: Ideally we need a new font for the arrows so we get the exact direction right, rather than just up, down, left, right...which I think Bruce was hinting at...:)[/COLOR]

Yup, that I was, and I couldn't find anything (free) that would work. But it's a mute point now.

> **kaivalagi said:**
> [COLOR="Blue"]Edit of edit: I've sorted output of a BF datatype and locale based WD output too, I just need those lists! Can't help myself...emailed yourself and jjgomera a copy :)[/COLOR]

I don't have the wingding fonts, I think one has to install the msfonts to get those, and then we'll need the number like you said. I'll download them and check them out.  :)

Chimo!
Bruce

By the way, **jjgomera** has put on the finishing touches to the Spanish Weather Conditions.  Here it is:
```
	conditions_text_es = {
        "0": _(u"Tornado"),
        "1": _(u"Tormenta Tropical"),
        "2": _(u"Huracán"),
        "3": _(u"Tormentas Fuertes"),
        "4": _(u"Tormentas"),
        "5": _(u"Lluvia y Nieve Mezclada"),
        "6": _(u"Lluvia y Aguanieve Mezclada"),
        "7": _(u"Aguanieve"),
        "8": _(u"Llovizna Helada"),
        "9": _(u"Llovizna"),
        "10": _(u"Lluvia engelante"), # o lluvia helada
        "11": _(u"Chaparrones"),
        "12": _(u"Chaparrones"),
        "13": _(u"Nieve Ligera"),
        "14": _(u"Nieve Ligera"),
        "15": _(u"Ventisca de nieve"),
        "16": _(u"Nieve"),
        "17": _(u"Granizo"),
        "18": _(u"Aguanieve"),
        "19": _(u"Polvo"),
        "20": _(u"Niebla"),
        "21": _(u"Bruma"),
        "22": _(u"Humo"),
        "23": _(u"Tempestad"),
        "24": _(u"Ventoso"),
        "25": _(u"Frío"),
        "26": _(u"Muy Nublado"),
        "27": _(u"Principalmente Nublado"),
        "28": _(u"Principalmente Nublado"),
        "29": _(u"Parcialmente Nublado"),
        "30": _(u"Parcialmente Nublado"),
        "31": _(u"Despejado"),
        "32": _(u"Despejado"),
        "33": _(u"Algo Nublado"),
        "34": _(u"Algo Nublado"),
        "35": _(u"Lluvia con Granizo"),
        "36": _(u"Calor"),
        "37": _(u"Tormentas Aisladas"),
        "38": _(u"Tormentas Dispersas"),
        "39": _(u"Tormentas Dispersas"),
        "40": _(u"Chubascos Dispersos"),
        "41": _(u"Nieve Pesada"),
        "42": _(u"Nevadas débiles y dispersas"),
        "43": _(u"Nevada Intensa"),
        "44": _(u"Nubes Dispersas"),
        "45": _(u"Tormentas"),
        "46": _(u"Nevadas Dispersas"),
        "47": _(u"Tormentas Aisladas"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
    }
```

---

### Post by kaivalagi on 2008-05-14
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Hi All,

I have just updated the script and details of this in the first post. The following has been done:

[LIST]
[*]Added French locale data - Thanks benpaka
[*]Added new BF (bearing font) datatype to provide an arrow character (use with Arrow.ttf font) as an alternative to the NSEW output from WD (wind direction) - Thanks for the idea jjgomera
[*]Updated WD output to be locale specific, currently supports default English, Spanish and French - Thanks Bruce M / jjgomera
[/LIST]

Make sure you install the Arrows.ttf font to use the BF datatype! I used inkscape and fontforge to create it, very easy to do.

I decided to take my break from development in installments ;)
....or until the wife won't put up with it any longer 8-[

I am such a script junkie!

---

### Post by Bruce M. on 2008-05-14
Hi Folks,

Thought I'd show you my "Spanish Weather" conky complete with the new **arrows font**, the idea came from jjgomera.

[CENTER]**Thanks JJ!**

[[IMG]http://img158.imageshack.us/img158/6607/arrows2mc7.th.jpg[/IMG]](http://img158.imageshack.us/my.php?image=arrows2mc7.jpg)[/CENTER]

So there you have it my conky on the right with today's weather and a 4 day forecast on the left done with only one "execi" call.

The "conkyForcast.py" script you can get from the first post.

If you want my "conkymain" (right), my "conkyforecast" conky (left) scripts or the "template" I'm using just ask, I'll be glad to post them.

Have a nice day.
Bruce

---

### Post by jjgomera on 2008-05-14
Hello
I've change my conky too with this update, the whole conky, so i've posted in this other thread: [http://ubuntuforums.org/showpost.php?p=4958136&postcount=2384](http://ubuntuforums.org/showpost.php?p=4958136&postcount=2384)

Thanks kaivalagi for the instant updates, whereas out there are very much thread with problem with this or that weather desklets =D>

---

### Post by kaivalagi on 2008-05-15
Any other ideas on scripts to create for Conky? 

Just remember we are limited to text only and the use of icons via fonts...

[COLOR="Blue"]Edit: I've decided I will knock up an email checker for both POP and IMAP next, give it details on mail server type, server name, username, password and whether to use ssl or not, and it will bring back a count of new messages...does that sound useful?

1st draft attached here if anyone wants to try it out! Take a look at the example conkyrc and template files, the script principles are the same as conkyForecast, but only a mail count is returned for now. I still need to figure out how I will provide the "new" email count for POP, currently it returns the total number of messages in the mailbox...
PM me with any questions, as this really shouldn't be on this thread :) If this turns out to be useful I'll create a new thread for it. Usage below.
Cheers

```
Usage: conkyEmail.py [options]

Options:
  -h, --help            show this help message and exit
  -mSERVERTYPE, --servertype=SERVERTYPE
                        servertype to check [default: POP] The server type
                        options are POP or IMAP
  -sSERVERNAME, --servername=SERVERNAME
                        server name to access [default: pop.mail.yahoo.co.uk]
                        The server name should be either a domain name or ip
                        address
  -e, --ssl             Use an SSL based connection.
  -uUSERNAME, --username=USERNAME
                        username to login with
  -pPASSWORD, --password=PASSWORD
                        Password to login with
  -tFILE, --template=FILE
                        define a template file to generate output in one call.
                        A displayable item in the file is in the form
                        {--servertype=POP --ssl
                        --servername=pop.mail.yahoo.com --username=joebloggs
                        --password=letmein}. Note that the short forms of the
                        options are not currently supported! None of these
                        options are applicable at command line when using
                        templates.
  -v, --verbose         request verbose output, not a good idea when running
                        through conky!


```

UPDATED: Email script was returning a count of 1 for no imap emails, fixed to return zero when none are there...
[/COLOR]

---

### Post by HippyRandall on 2008-05-17
All I can say is WOW! Great work on this.
I have noticed since using this template idea that python is always in the top 3 of my processes in conky. Is this caused by the script do you think?
Not done playing around with this yet but I have gotten some great ideas from the 16 pages before this one. (Yes I read all the posts...talk about eye strain.:lolflag: )

[COLOR="Blue"]Edit: nevermind about the python thing I mentioned. All works well now. just need to work out the "No connection" "no information available" problems. I know I saw it somewhere here :)[/COLOR]

[COLOR="Blue"]2nd Edit: rather than mess around with a bunch of stuff I simply changed the long string on no connection to be just "Not Connected" Better than having a screen full of a long string of words for me.[/COLOR]

---

### Post by kaivalagi on 2008-05-17
> **HippyRandall said:**
> All I can say is WOW! Great work on this.
I have noticed since using this template idea that python is always in the top 3 of my processes in conky. Is this caused by the script do you think?
Not done playing around with this yet but I have gotten some great ideas from the 16 pages before this one. (Yes I read all the posts...talk about eye strain.:lolflag: )

Glad you find the script useful, any suggestions just fire away!

Good to see you are reading all the details too, it's always good to have someone else about who knows a thing or two about this script :)

> **HippyRandall said:**
> [COLOR="Blue"]Edit: nevermind about the python thing I mentioned. All works well now. just need to work out the "No connection" "no information available" problems. I know I saw it somewhere here :)[/COLOR]

When you update the script from a  previous version (I am presuming you've done this?) the best thing to do is delete the cached files in the /tmp directory. Those files are a "pickled" version of the class data used in the script, if the class structure changes between versions they can cause various issues.

Just run the following and try the latest script again:

```
rm /tmp/conkyForecast*
```

Hope that helps :)

---

### Post by Bruce M. on 2008-05-17
> **kaivalagi said:**
> Those files are a "pickled" version of the class data used in the script, if the class structure changes between versions they can cause various issues.

pickled? When I think pickled I think:

Heinz, or
Booze

How the heck does **pickled** snakes (python; yea yea i know, Monty) figure into this?

In other words: What does pickled mean?

And one more question: Are you going to start a new thread for your email "pickled python" ?

Have a good one.
Bruce

I gotta look at that one....

---

### Post by HippyRandall on 2008-05-17
the problem comes up after logging in  and the wireless network isn't up and running yet. my startup script looks like this:
#!/bin/bash

```
sleep 20 &&
conky -c ~/.conkyrc &
sleep 10 &&
conky -c /home/hippy/conkyweatherrc
exit
```

should I increase the sleep time to 20 or more on the weatherrc portion?

---

### Post by Bruce M. on 2008-05-17
> **HippyRandall said:**
> the problem comes up after logging in  and the wireless network isn't up and running yet. my startup script looks like this:
#!/bin/bash

```
sleep 20 &&
conky -c ~/.conkyrc &
sleep 10 &&
conky -c /home/hippy/conkyweatherrc
exit
```

should I increase the sleep time to 20 or more on the weatherrc portion?

If your wireless isn't working after 30 seconds (20 + 10) try increasing the weather conky in steps of 5 ... 15, 20, 25 until it works.

---

### Post by kaivalagi on 2008-05-17
> **HippyRandall said:**
> the problem comes up after logging in  and the wireless network isn't up and running yet. my startup script looks like this:
#!/bin/bash

```
sleep 20 &&
conky -c ~/.conkyrc &
sleep 10 &&
conky -c /home/hippy/conkyweatherrc
exit
```

should I increase the sleep time to 20 or more on the weatherrc portion?

Interesting issue

The double &&'s in your shell script are normally used to have multiple commands run in a one line command e.g. "task1 && task2" would run task1 and then task2, I am not sure whether _they_ are causing the issue here...

Could you first off try changing the script to this:

```
sleep 20
conky -c ~/.conkyrc &
sleep 10
conky -c ~/conkyweatherrc &
exit
```

Also, below is the sort of thing I use in an attempt to wait until gnome is up and running properly, before I run conky tasks. Make sure USERNAME is replaced with your own! the pgrep call is user specific. I also have an extra wait state for 10 seconds just in case :) If you're not running gnome you could replace gnome-session with whatever suits...

```

#!/bin/sh

	while true; do

	    if [ $(pgrep -u,USERNAME gnome-session) > 0 ]; then

		# wait an extra 10 seconds just in case!
		sleep 10

		conky -c ~/Scripts/conky/conkyrc-music &
		conky -c ~/Scripts/conky/conkyrc-strip &
		conky -c ~/Scripts/conky/conkyrc-email &

		break; # exit out of while loop
	    else

		sleep 1; # wait before checking for gnome-session again
	    fi
	done 
```

Maybe I need to tweak the script a little, the script should use whatever the contents of the cached files are, if it can't get a connection and they are there from a previous call. That _should_ solve the issue as long as the cached files exist from a previous call...I could have got something wrong, it's been known to happen before :)

Until I figure something out to future proof conkyForecast, I suggest you play around with what I've suggested for your shell script.

Hope that helps

---

### Post by kaivalagi on 2008-05-17
> **Bruce M. said:**
> pickled? When I think pickled I think:

Heinz, or
Booze

How the heck does **pickled** snakes (python; yea yea i know, Monty) figure into this?

In other words: What does pickled mean?


Funny how the term "pickling" is used in python. In every other development language I know it is known as serialization. If you look at the python docs for pickling, "serialization" is mentioned though.

Serialization basically involves taking an class, i.e. something with a structure, and converting it into a stream of text (usually xml) for storing away/transforming into readable data etc. Pickling in this sense therefore means preserving something for using later. Unpickling is the reverse. Can you unpickle an egg? lol

> **Bruce M. said:**
> 
And one more question: Are you going to start a new thread for your email "pickled python" ?

Have a good one.
Bruce

I gotta look at that one....


I wonder if you can eat pickled python anywhere? 

I'll have to come up with a new python project where Ubuntu itself is serialized! We could then have project names of "pickled gibbon", "pickled heron" and "pickled ibex" :lolflag:

Seriously though, pickling in python is one of the better functions, it is very easy to do in comparison to other languages. Python really does kick butt when it comes to simplifying things, even when the naming of functions is sometimes a bit off the wall...

---

### Post by HippyRandall on 2008-05-17
[http://www.dafont.com/moon-phases.font]("http://www.dafont.com/moon-phases.font") Found this site with the moon phases font that is free for personal use. I know someone was talking about using a font for the phases and I was going to attempt to help out and make one but ummm...yeah that was alot harder than I thought. How can we implement this into conky?

---

### Post by kaivalagi on 2008-05-18
> **HippyRandall said:**
> [http://www.dafont.com/moon-phases.font]("http://www.dafont.com/moon-phases.font") Found this site with the moon phases font that is free for personal use. I know someone was talking about using a font for the phases and I was going to attempt to help out and make one but ummm...yeah that was alot harder than I thought. How can we implement this into conky?

There is no straight forward way, the script doesn't support it at the moment.

To support it would require some development. There is a moon icon returned in the xml weather data, this can be used to index the correct font character. A new datatype for the moon font (MF) would need to be added, and all the code to interpret the data would get driven off this.

[COLOR="Blue"]Edit:
Just had a quick play with the code and the only thing I don't know is which icon number relates to which moon phase...it is not documented in the sdk for weather.com...

I am currently outputting the icon number instead of a character, so someone will need to run the script and record each number in relation to the phase text outputted, as and when they are output. Once all are known the script can be updated...hope that makes sense. 

I'll update the script in the first post with this feature in the next 15 minutes (look for dev notes for moon font).[/COLOR]

---

### Post by HippyRandall on 2008-05-18
looking at the page source for [http://www.weather.com/documentation/xml/weather.dtd]("http://www.weather.com/documentation/xml/weather.dtd") it seems that there are alot of possibilities for displaying all kinds of info. Off the top of my head I can think of "Feels Like" and "Dew Point" being especially handy. For seafaring types I can see "Wave Height" and other such info as being desirable.

I have been googling around and have only come up with a few moon icon codes:

```
1 Waxing Crescent
2
3
4 [COLOR="Blue"]Waxing Crescent[/COLOR]
5
6
7
8
9
10
11
12
13 Waxing Gibbous
14
15 Full
16
17
18
19
20 [COLOR="Blue"]Waning Gibbous[/COLOR]
21
22
23
24
25
26
27
28
29
30
```
I will update this post with blue text as I find more.

---

### Post by Apex-jb on 2008-05-18
Thanks for the script. Finally a weather script that actually worked for me. I have one question though, what exactly is the code I need to change the color of what is displayed? Currently the rest of my conky is using 0077ff but the default, which is what the weather script is using, is white. I tried this line to see if it would work but it made the city name disappear and everything else appear hot pink.
```
${color #0077ff execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CN --refetch}
```

Here is the code I am using.
```
Weather:
${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CN --refetch}

Day: ${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=DW}
Conditions: ${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CC}
${font Weather:size=36}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=WF}${font}
Temp: ${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=HT}
Wind: ${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=WS}
Wind Direction: ${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=WD}
Humidity: ${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=HM}
```

---

### Post by HippyRandall on 2008-05-18
Try changing:
> **Apex-jb said:**
> 
```
${color #0077ff execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CN --refetch}
```

[/CODE]

To:

```
${color #0077ff} {execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CN --refetch}
```

I am still new to this weather scripting so I am not 100% on that change but it can't hurt to give it a shot

---

### Post by kaivalagi on 2008-05-18
> **Apex-jb said:**
> Thanks for the script. Finally a weather script that actually worked for me. I have one question though, what exactly is the code I need to change the color of what is displayed? Currently the rest of my conky is using 0077ff but the default, which is what the weather script is using, is white. I tried this line to see if it would work but it made the city name disappear and everything else appear hot pink.
```
${color #0077ff execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CN --refetch}
```


Needs to be something like:

```

${color #0077ff}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CN --refetch}
```

Each setting is "encased" like this: ${ setting }
They need to be on their own in between a starting "${" and ending "}" otherwise conky doesn't know what to do...

If you go to the conky sourceforge site you'll find documentation and also example conky files. Start here: [http://conky.sourceforge.net]("http://conky.sourceforge.net")

There have also been some good conkyrc's posted in the forums before now, a select few are in this thread, the rest can be found by searching for "conkyrc"

Hope that helps

[COLOR="Blue"]Edit: HippyRandall is fast! :)
Not sure if you'll get by without the $ sign before the execi section?[/COLOR]

---

### Post by Apex-jb on 2008-05-18
Thanks, got it working.

EDIT: One more thing, how do I get it to display English units?

---

### Post by HippyRandall on 2008-05-18
> **kaivalagi said:**
> Needs to be something like:

Each setting is "encased" like this: ${ setting }
They need to be on their own in between a starting "${" and ending "}" otherwise conky doesn't know what to do...

[COLOR="Blue"]Edit: HippyRandall is fast! :)
Not sure if you'll get by without the $ sign before the execi section?[/COLOR]

I totally missed that extra $ missing from my post. Glad you caught it. Been pouring over a TON of google results in regards to the moon phases and that list a couple posts up is all I can find. I am assuming that 30 should be "New" or something similar. If anyone else can find a resource for the icons, be my guest. My eyes are strained from all the code reading and my scroll finger is going numb. :lolflag:

---

### Post by HippyRandall on 2008-05-18
> **Apex-jb said:**
> Thanks, got it working.

EDIT: One more thing, how do I get it to display English units?

you have to use the --imperial flag in a template file 

```
Current: {--datatype=CC --startday=0 --imperial}
```

or -i in your regular conky execi calls similar to this:

```
Wind Speed: ${execi 3600 python ~/conky/conkyForecast.py --location=USME0356 --datatype=WS -i}
```

---

### Post by Bruce M. on 2008-05-18
> **HippyRandall said:**
> looking at the page source for [http://www.weather.com/documentation/xml/weather.dtd]("http://www.weather.com/documentation/xml/weather.dtd") it seems that there are alot of possibilities for displaying all kinds of info. Off the top of my head I can think of "Feels Like" and "Dew Point" being especially handy. For seafaring types I can see "Wave Height" and other such info as being desirable.

I like the "Feels Like" and "Dew Point" Plus I think there is "VU" something about Ultra Violet levels... that would be nice.

> **HippyRandall said:**
> I have been googling around and have only come up with a few moon icon codes:

I think this is what you are looking for:

OK ---- using UPPER Case letters and "0" and "1"
The * depicts the actual point of the New Moon, Waxing Crescent, 1st Quarter, Full Moon, Waning Gibbous, Last Quarter and Waning Crescent for the 28 day cycle, which isn't exact.

Using:
View Fonts: [http://www.dafont.com/moon-phases.font](http://www.dafont.com/moon-phases.font)
View what they are: [http://aa.usno.navy.mil/faq/docs/moon_phases.php](http://aa.usno.navy.mil/faq/docs/moon_phases.php)

Where I see: Following waning crescent is New Moon, beginning a repetition of the complete phase cycle of 29.5 days average duration. The time in days counted from the time of New Moon is called the Moon's "age". Each complete cycle of phases is called a "lunation".


01 -"1" - New Moon *
02 - A - Waxing Crescent
03 - B - Waxing Crescent
04 - C - Waxing Crescent &
       - Waxing Crescent *
05 - D - Waxing Crescent &
06 - E - Waxing Crescent
07 - F - Waxing Crescent
08 - G - First Quarter *
09 - H - Waxing Gibbous
10 - I - Waxing Gibbous
11 - J - Waxing Gibbous &
       - Waxing Gibbous *  
12 - K - Waxing Gibbous &
13 - L - Waxing Gibbous   <<-- I see the 13 today ( Sun 18 May 2008 )
14 - M - Waxing Gibbous
15 - "0" - Full Moon *
16 - N - Waning Gibbous
17 - O - Waning Gibbous
18 - P - Waning Gibbous &
       - Waning Gibbous * 
19 - Q - Waning Gibbous &
20 - R - Waning Gibbous
21 - S - Waning Gibbous
22 - T - Last Quarter *
23 - U - Waning Crescent
24 - V - Waning Crescent
25 - W - Waning Crescent &
       - Waning Crescent *
26 - X - Waning Crescent &
27 - Y - Waning Crescent
28 - Z - Waning Crescent
01 - "1" - New Moon *

Now unless you can claculate a 29.5 day cycle for this I would suggest only using:

```
Font	When Site says:
"1"	- New Moon *
 C	- Waxing Crescent &
 G	- First Quarter *
 K	- Waxing Gibbous &
 "0"	- Full Moon *
 Q	- Waning Gibbous &
 T	- Last Quarter *
 X	- Waning Crescent &
 "1"	- New Moon *
```

We'll only need 8 images in the font.
So what do you think?
Bruce

**EDIT:** *Stranger Than Fiction!*

One can say: ( Sun 18 May 2008 )
But if you remove the spaces you get: (Sun 18 May 2008)

---

### Post by Bruce M. on 2008-05-18
> **kaivalagi said:**
> Funny how the term "pickling" is used in python. In every other development language I know it is known as serialization. If you look at the python docs for pickling, "serialization" is mentioned though.

Serialization basically involves taking an class, i.e. something with a structure, and converting it into a stream of text (usually xml) for storing away/transforming into readable data etc. Pickling in this sense therefore means preserving something for using later. Unpickling is the reverse. Can you unpickle an egg? lol

Try standing downwind after I eat a few and then you tell me!

> **kaivalagi said:**
> I wonder if you can eat pickled python anywhere?

You know, I'll just bet you can. Not sure that it would go on my personal delicacy list though.

> **kaivalagi said:**
> I'll have to come up with a new python project where Ubuntu itself is serialized! We could then have project names of "pickled gibbon", "pickled heron" and "pickled ibex" :lolflag:

Oh darn, I thought you said "pickled herring" there for a sec.  :)

> **kaivalagi said:**
> Seriously though, pickling in python is one of the better functions, it is very easy to do in comparison to other languages. Python really does kick butt when it comes to simplifying things, even when the naming of functions is sometimes a bit off the wall...

OK, now that we understand each other pass the dill pickles please.  :)

Have a good one
Bruce

---

### Post by HippyRandall on 2008-05-18
What do I think? I think Bruce M. steps up to the plate and hits another great hit! Where did you find these? I looked and looked till I thought my eyes would bleed.

Looking at the weather fonts included in the first post I see the moon in 10 phases. Now we have a starting place as well as a couple different fonts to go with. The one in the original post shows this info in the copyright field:

```
1.0, (c)1994 Jonathan Macagba. Send $5: Box 14013 Phila. 19122
```Not sure but this seems like the "donation" type request and the dafont website did say free for personal use.

I am trying to learn here so pardon my ignorant questions. How do we go about implementing this?  I would like to have the steps explained so feel free to email me or pm me.

[COLOR=Blue]Can you possibly give me a couple good links for learning how to parse xml with python so I can learn and not bug you guys with question after question?[/COLOR]

---

### Post by Bruce M. on 2008-05-19
> **HippyRandall said:**
> What do I think? I think Bruce M. steps up to the plate and hits another great hit! Where did you find these? I looked and looked till I thought my eyes would bleed.

In Google I typed: Moon Phases and let it rip.
That US Navy site was maybe the third one down, can't remember.  :)

> **HippyRandall said:**
> Looking at the weather fonts included in the first post I see the moon in 10 phases. Now we have a starting place as well as a couple different fonts to go with. The one in the original post shows this info in the copyright field:

```
1.0, (c)1994 Jonathan Macagba. Send $5: Box 14013 Phila. 19122
```Not sure but this seems like the "donation" type request and the dafont website did say free for personal use.

Oh, that's not good.

> **HippyRandall said:**
> I am trying to learn here so pardon my ignorant questions. How do we go about implementing this?  I would like to have the steps explained so feel free to email me or pm me.

[COLOR=Blue]Can you possibly give me a couple good links for learning how to parse xml with python so I can learn and not bug you guys with question after question?[/COLOR]

I'm not a programmer, and I'm learning as well. kaivalagi told me what to install once but I have done a clean install of Xfce 8.04 since and don't have the programs, I have to search his emails I have saved to find what to install.  :)

kaivalagi: Your turn at bat, seems you have two people now interested in learning to help you.  :)

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-05-19
Seems I was off a little in my original list:

00 - #L - Phrase

00 - indicates the number output by the MF command
#L - indicates moon image the "moon font" will use
Phrase - indicates the text output from the MP command

I will edit "this post" daily until we see a clear pattern.
```

00 -"1" - New Moon
01 - A - Waxing Crescent
02 - B - Waxing Crescent
03 - C - Waxing Crescent
04 - D - Waxing Crescent
05 - E - Waxing Crescent
06 - F - Waxing Crescent
07 - G - First Quarter
08 - H - Waxing Gibbous
09 - I - Waxing Gibbous
10 - J - Waxing Gibbous
11 - K - Waxing Gibbous
12 - L - Waxing Gibbous
13 - M - Waxing Gibbous   <- 18 May; MP: Waxing Gibbous - MF:13 
14 - "0" - Full Moon      <- 19 May; MP: Full - MF: 14
15 - "0" - Full Moon      <- 20 May; MP: Full - MF: 15 ???

15 - N - Waning Gibbous   <- ? ?

16 - O - Waning Gibbous   <- 21 May; MP: Waning Gibbous - MF: 16
16 - O - Waning Gibbous   <- 22 May; MP: Waning Gibbous - MF: 16 - this morning
17 - P - Waning Gibbous   <- 22 May; MP: Waning Gibbous - MF: 17 - @ 21:21 GMT
17 - P - Waning Gibbous   <- 23 May; MP: Waning Gibbous - MF: 17 - @ 14:02 GMT
18 - Q - Waning Gibbous   <- 23 May; MP: Waning Gibbous - MF: 18 - @ 16:08 GMT
18 - Q - Waning Gibbous   <- 24 May; MP: Waning Gibbous - MF: 18 - @ 10:51 GMT
19 - R - Waning Gibbous   <- 24 May; MP: Waning Gibbous - MF: 19 - @ 23:12 GMT
19 - R - Waning Gibbous   <- 25 May; MP: Waning Gibbous - MF: 19 - @ 16:44 GMT
20 - S - Waning Gibbous   <- 25 May; MP: Waning Gibbous - MF: 20 - @ 22:17 GMT
20 - S - Waning Gibbous   <- 26 May; MP: Waning Gibbous - MF: 20 - @ 18:27 GMT
21 - T - Last Quarter     <- 26 May; MP: Last Quarter - MF: 21(T) - @ 22:30 GMT
21 - T - Last Quarter     <- 26 May; MP: Last Quarter - MF: 21(T) - @ 02:13 GMT
22 - U - Waning Crescent
23 - V - Waning Crescent
24 - W - Waning Crescent
25 - X - Waning Crescent
26 - Y - Waning Crescent
27 - Z - Waning Crescent

```Have a nice full moon
Bruce

**NOTES: **Obviously I was wrong about needing only 8 fonts
[LIST=1]
[*]May 19th and 20th; MP read "Full Moon" but used two different fonts #14 and #15
[LIST][*]Looks like we'll have to wait a month to see if it uses "two" moon fonts for "full moon" again.[/LIST]
[*]May 22nd; started with MF 16 and ended with MF 17
[*]May 23rd; started with MF 17 and ended with MF 18
[*]May 25th; understandable that the MF changes midday it's night somewhere.  :)
[*]**_May 26th - Sometime tonight I'm hoping that:_**
[LIST]
[*]20 - S - Waning Gibbous   <- 26 May; MP: Waning Gibbous - MF: 20 - @ 18:27 GMT, **changes to:**
[*]21 - T - Last Quarter   <- 26 May; MP: Last Quarter - MF: 21
[/LIST] 
[/LIST]

**[COLOR="Red"]Last Edit:[/COLOR]** Done, see post [209]("http://ubuntuforums.org/showpost.php?p=5045197&postcount=209"), [213]("http://ubuntuforums.org/showpost.php?p=5048350&postcount=213") & [214]("http://ubuntuforums.org/showpost.php?p=5051197&postcount=214")

Have a nice day
Bruce

---

### Post by kaivalagi on 2008-05-19
> **HippyRandall said:**
> [COLOR=Blue]Can you possibly give me a couple good links for learning how to parse xml with python so I can learn and not bug you guys with question after question?[/COLOR]

I'll attempt at getting you on the right track.

**1-Environment**
First off if you have gedit, start with that for editing python, it handles all the syntax coloration etc. Once you get established then move on to something a little more meaty, I use Eclipse with the PyDev plugin. The benefit of a decent dev environment is that you can debug code and see what is happening bit by bit, 'watching' variable data as you go etc. PyDev also has intellisense which can help as great deal. All the software I have mentioned is available in the repo's.

**2-SDK and XML Examples**
Download the SDK for weather.com xoap (you need to register, then you'll receive a couple of emails, start here: [http://www.weather.com/services/xmloap.html]("http://www.weather.com/services/xmloap.html")). Also download some sample xml from the website, as would be downloaded by conkyForecast.py, so you know what's being messed about with. Use a url in the form of below (with your location code and registration details if you have some maybe):
```
http://xoap.weather.com/weather/local/UKXX0103?cc=*&dayf=5&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b
```

**3-Try to follow conkyForecast**
Search for the fetchData method in conkyForecast.py, it is responsible for the retrieving and storing of the xml content. The section of code entitled *"# interrogate weather data, load into class structure and pickle it"* is used to extract the xml data for current, day forecast and night forecast and load it into 3 classes. These classes are then stored in 'pickled' files in your /tmp/ directory for use in output the next time round, unless fresh data is required.
You're best trying to follow this code whilst looking at the xml it is extracting data from, you should see the pattern...

Bottom line, get stuck in, don't be afraid to mess things up, just keep a decent working backup!

Some url's worth going to:
1) [http://learnpython.pbwiki.com/HowToStart]("http://learnpython.pbwiki.com/HowToStart")
2) [http://www.python.org/doc/]("http://www.python.org/doc/")
3) [http://docs.python.org]("http://docs.python.org")

Hope that helps

---

### Post by kaivalagi on 2008-05-19
> **Bruce M. said:**
> 
Have a nice full moon
Bruce

Arrrwwwhhhooooooooooooooooooo!

---

### Post by HippyRandall on 2008-05-19
Thanks for the help on this kaivalagi. I have gedit and use it regularly so I am going to stick with that for now. I will check out Eclipse in the future though.
I set up an account with weather.com to get the XML subscription. Was that the right one? I still have not received an email with the SDK and license number though. I wonder if it just takes a couple days or if I signed up for the wrong thing.
Checking out those links now and I have to say that the best way for me to learn is to open up your py script and tear into it looking for logical things I can follow so thanks for: *"# interrogate weather data, load into class structure and pickle it". *oh and I never work on a live copy...learned that the hard way. :lolflag:

---

### Post by HippyRandall on 2008-05-19
Question
I see on lines 1131 and 1332 of conkyForecast.py you have: 

```
                current_temp_feels_n = current_condition_n.getElementsByTagName('flik')[0]
                current_temp_feels = self.getText(current_temp_feels_n.childNodes)

```

So I assume that you are already grabbing this data. How can I output this in conky? Obviously at this time of year the wind chill is not a factor but in Dec and Jan it can be very important. Also a 'feels like" for summer time can be helpful.

Just trying to pick my way through the code so if I am wrong somewhere please point it out.

---

### Post by kaivalagi on 2008-05-19
> **HippyRandall said:**
> Thanks for the help on this kaivalagi. I have gedit and use it regularly so I am going to stick with that for now. I will check out Eclipse in the future though.
No worries, you might find eclipse can help you understand the code a little better though, but you'll need to learn how to use it first :) If you stick with the gedit route then get to know the print function, this is your friend! You can put a print in place here and there to get an idea of what data variables are holding etc. 

> **HippyRandall said:**
> I set up an account with weather.com to get the XML subscription. Was that the right one? I still have not received an email with the SDK and license number though. I wonder if it just takes a couple days or if I signed up for the wrong thing.
Checking out those links now and I have to say that the best way for me to learn is to open up your py script and tear into it looking for logical things I can follow so thanks for: *"# interrogate weather data, load into class structure and pickle it". *oh and I never work on a live copy...learned that the hard way. :lolflag:

It might take a day or 2 for the emails to come, but you should receive one relating to the sdk. If you don't in the next 2 days let me know and I'll email you the zip they sent me.

Try knocking up a simple program that will output something in the terminal, then move that code into a function and call it. etc etc until you get a feel for how python hangs together.

> **HippyRandall said:**
> Question
I see on lines 1131 and 1332 of conkyForecast.py you have: 

```
                current_temp_feels_n = current_condition_n.getElementsByTagName('flik')[0]
                current_temp_feels = self.getText(current_temp_feels_n.childNodes)

```

So I assume that you are already grabbing this data. How can I output this in conky? Obviously at this time of year the wind chill is not a factor but in Dec and Jan it can be very important. Also a 'feels like" for summer time can be helpful.

Just trying to pick my way through the code so if I am wrong somewhere please point it out.

Yes, the xml data extraction is more or less complete, that was done up front based on the xml structure from a while back. The xml data structure have changed a little since though.

After the lines you mentioned above you'll see a line starting "current_conditions_data = WeatherData("

This line is responsible for creating of a class that holds particular data from the xml that is used in the output. The next line takes the newly constructed class and adds it to a list (the .append line).

This class data is then pickled and used by the getOutput function later on.

If you want more datatypes such as a feels like then the class needs to hold this data, and the getOutput function needs to get it for you if you request it (new datatype option).

You really need to learn how to follow the code, I can't explain every single step via email, Bruce can bear witness to how difficult that is. For that you need either a basic understanding of code in general through experience/reading (functions, classes, objects etc), or you can step through each line of code using eclipse and pydev, looking at things 1 line at a time.

Why don't you take an example call you could make to the script, say --datatype=HT and try to understand as you go through the code what is happening and why, at the end of the file are the main function calls, start there.

If that proves a little tricky, it's worth seeking the help of some of the developers in the programming forums on ubuntuforums, some can be arrogant, but for the most part people are really helpful and would no doubt have a good idea of starting material for a python newbie to read...

Hope that helps...

---

### Post by kaivalagi on 2008-05-21
[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]

As HippyRandall/Bruce had shown an interest, I have just updated the script to output *"feels like"* temperature for current conditions. All I did in the end was populate the current conditions low temp class data with the feels like data.

So....
[LIST]
[*] To get current condition temp use --datatype=HT (as was the case before)
[*]To get current condition *"feels like"* temp use --datatype=LT. 
[/LIST]

Previously both datatype options gave current temp when used for current conditions, so if you are using the LT option for current temp you need to switch over to use HT instead.

Also note that the use of HT and LT is unchanged for forecast temperatures, i.e. any output requested with a --startday=... option

Grab the latest tar.gz from the 1st post for the updated script

Cheers

---

### Post by zeny on 2008-05-21
I keep getting this: 

> riban@rounz:~/scripts$ conky 
Conky: use_spacer should have an argument of left, right, or none.  'yes' seems to be some form of 'true', so defaulting to right.
Conky: desktop window (10000ab) is subwindow of root window (13b)
Conky: window type - override
Conky: drawing to created window (2c00001)
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/riban/.scripts/conkyForecast.py", line 1292, in <module>
    weather.outputData()
  File "/home/riban/.scripts/conkyForecast.py", line 1265, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/riban/.scripts/conkyForecast.py", line 861, in getOutputText
    output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
IndexError: list index out of range
Conky: received SIGINT or SIGTERM to terminate. bye!


I think I've messed up!

---

### Post by zeny on 2008-05-21
> **kaivalagi said:**
> I thought I'd post my conky setup

I am using a template to get weather data in one call, and calling again for the weather font output twice...3 execi calls in all for my weather output.

I've attached my conkyrc and the template file it refers to.

No doubt the layout needs adjusting for any font changes, and really I should probably use mono fonts to ensure the layout is always neat and tidy...time will tell what I need to do w.r.t. fonts etc

Hopefully this is a starter for most when it comes to a working usable conkyForecast template anyway

Enjoy :)

I really really like yours, I tried copying but didn't work, could you also include the fonts :D

---

### Post by HippyRandall on 2008-05-21
cool thanks. I'll try this out soon. I tried to define a new datatype for <flik> but royally borked something. I thought I was following along with your code but I must have screwed something up somewhere. I decided that I would instead go and follow the tut at pythondocs.org to better understand the language. Slow going but I'll get there.

---

### Post by kaivalagi on 2008-05-21
> **HippyRandall said:**
> cool thanks. I'll try this out soon. I tried to define a new datatype for <flik> but royally borked something. I thought I was following along with your code but I must have screwed something up somewhere. I decided that I would instead go and follow the tut at pythondocs.org to better understand the language. Slow going but I'll get there.

No worries, if you get stuck PM with any questions and I'll try to set you straight

---

### Post by kaivalagi on 2008-05-21
> **zeny said:**
> I keep getting this: 

```

riban@rounz:~/scripts$ conky
Conky: use_spacer should have an argument of left, right, or none. 'yes' seems to be some form of 'true', so defaulting to right.
...
...
WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
IndexError: list index out of range

```

I think I've messed up!

1) I am using an older version of conky not available in the repos (1.49 which supports xmms2 output). The issue above raised about use_spacer is due to a change in the conky settings required in the hardy repo's conky. Either take the use_spacer setting out or follow the instructions the error is giving you and change yes to left for example.

2) list index out of range may be because the template is using a startday greater than 4, weather.com brought in a restriction to 5 days of forecasting (incl todays weather) after I posted the example. Make sure no --startday==5 or --endday=5 exists in the config or template...

> **zeny said:**
> I really really like yours, I tried copying but didn't work, could you also include the fonts :D

I attached other fonts I have used in the past, which are not in the first post. Check out the first post for details on how to install fonts.

All the fonts are freely available on the net, a good place to start is [http://www.dafont.com/]("http://www.dafont.com/")

Another good place to check out is [http://gnome-look.org/]("http://gnome-look.org/")

If installing the attached fonts doesn't fix things, try changing the font settings in the conkyrc to something that you know works. Failing that post back the errors you get when running conky from the terminal window, and we can see what is going on (hopefully)

Hope that helps
]

---

### Post by zeny on 2008-05-21
Cool! Thanks I got it to kinda work nice, I now have no errors and see the current weather. 

Thing is it displays todays weather but stops at Thu (See attachment)

---

### Post by kaivalagi on 2008-05-22
> **zeny said:**
> Cool! Thanks I got it to kinda work nice, I now have no errors and see the current weather. 

Thing is it displays todays weather but stops at Thu (See attachment)

Post your conkyrc and template files

Looks to me like you still have an error of sorts...

---

### Post by zeny on 2008-05-22
Actually I just used yours, I just changed /home/mark/Scripts to my directory and changed your location code. Then I removed day 5 like you mentioned. Thats it, I'm at work now so I'll have to post again later. Odd thing is even with the information you posted on the first page I get the same results. I'm using the latest in the repos for Hardy 8.04.

---

### Post by kaivalagi on 2008-05-22
> **zeny said:**
> Actually I just used yours, I just changed /home/mark/Scripts to my directory and changed your location code. Then I removed day 5 like you mentioned. Thats it, I'm at work now so I'll have to post again later. Odd thing is even with the information you posted on the first page I get the same results. I'm using the latest in the repos for Hardy 8.04.

Strange, looks like the output is getting truncated, you shouldn't need to, but try adding the below to the config settings in your conkyrc:

```
text_buffer_size 256
```

Also, try running the python script outside of conky by taking out the section of text after each execi statement, and run it in the terminal window to see what you get...i.e. run something like the below based on what you have in your conkyrc:

```
python conkyForecast.py --location=XYZ --template=/path/to/template/file
```

If all else fails, post your conkyrc and template and I can debug it to see what is going on with what you are using...I know you've said you just used what I posted, but I would want to make sure I am testing exactly what you are using.

Hope that helps.

---

### Post by DShroud on 2008-05-22
I'm having strange problems so far with this weather script.  First here is a screenshot of what is going on...

[[img]http://img169.imageshack.us/img169/9050/conky1kq4.th.png[/img]](http://img169.imageshack.us/my.php?image=conky1kq4.png)

For some reason it can't load the weather fonts, even after I've followed all the instructions you posted.  It is still displaying the strange characters next to the Fahrenheit and Celsius symbols.  Here is my .conkyrc...

```


override_utf8_locale yes
text_buffer_size 256

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft no

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color green}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color green}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${hwmon 0 temp 1}C
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color green}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Linux: ${fs_free_perc /}%   ${fs_bar 6 /}$color
Media: ${fs_free_perc /media/media}%   ${fs_bar 6 /media/media}

${color green}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color green}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color green}WEATHER${hr 2}$color

${color}Location: Torrington, CT

${color #B3B3B3}Condition: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=CC}
Temperature: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -i}
Forecast: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=0 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --startday=0 --datatype=LT -i}
Humidity: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=HM}
Wind: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=WS -i}
${alignr}${voffset -58}${offset -70}${font weather:size=45}${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=WF}$font
${voffset 15}${color ffffff}3 day forecast
${voffset 7}${color #B3B3B3}${offset 13}${execi 3600 python /home/justin/.scripts/conkyForecast.py -w --location=08628 --startday=1 --endday=5 --datatype=DW --spaces=7}
${font weather:size=33}${offset 6}${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --startday=1 --endday=5 --datatype=WF} $font
${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=1 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=1 --datatype=LT -i} ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=2 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=2 --datatype=LT -i} ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=3 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=3 --datatype=LT -i} ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=4 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=4 --datatype=LT -i} ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=5 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=5 --datatype=LT -i}

```

---

### Post by Bruce M. on 2008-05-22
> **DShroud said:**
> I'm having strange problems so far with this weather script.

I was going to suggest: override_utf8_locale yes, but I see you have it.

Second option...
Change: use_xft no to [COLOR="Blue"]use_xft yes[/COLOR]

That might clear up both of your problems.

Have a nice day.
Bruce

---

### Post by jjgomera on 2008-05-22
> **DShroud said:**
> I'm having strange problems so far with this weather script.  First here is a screenshot of what is going on...

[[img]http://img169.imageshack.us/img169/9050/conky1kq4.th.png[/img]](http://img169.imageshack.us/my.php?image=conky1kq4.png)

For some reason it can't load the weather fonts, even after I've followed all the instructions you posted.  It is still displaying the strange characters next to the Fahrenheit and Celsius symbols.  Here is my .conkyrc...

i think fonts name is case sensitive, so, you may change it to Arial and Weather

---

### Post by kaivalagi on 2008-05-22
> **DShroud said:**
> I'm having strange problems so far with this weather script.
...
For some reason it can't load the weather fonts, even after I've followed all the instructions you posted.  It is still displaying the strange characters next to the Fahrenheit and Celsius symbols.  Here is my .conkyrc...


Nothing wrong with the script itself, it's all down to the conky settings for forecast ranges and fonts.

1) Your conky settings for the script use start and end days up to 5, this will break. I did post some way back in the thread about the limit to forecasting, now the max is a start or end day of 4 (not 5/6/7/8 as before). I'll add the detail to the first post also.

2) The font rendering needs to be done using xft, so the weather font works, so this:

```
use_xft no
```

becomes this:

```
use_xft yes
xftfont Arial:size=9
```

Change the font to your liking...and because we are now using xft the following was commented out:

```
#font arial
```

All the modifications to your conkyrc are below. You may need to mess around with the layout now I have removed one forecast day

**[COLOR="Red"]!!![/COLOR]** I highly recommend that you move a lot of the weather output into a template(s), so you can have a single execi call to cover off a lot of the output. This will speed it up a great deal...

```
override_utf8_locale yes
text_buffer_size 256

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes
xftfont Arial:size=9

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color green}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color green}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${hwmon 0 temp 1}C
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color green}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Linux: ${fs_free_perc /}%   ${fs_bar 6 /}$color
Media: ${fs_free_perc /media/media}%   ${fs_bar 6 /media/media}

${color green}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color green}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color green}WEATHER${hr 2}$color

${color}Location: Torrington, CT

${color #B3B3B3}Condition: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=CC}
Temperature: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -i}
Forecast: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=0 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --startday=0 --datatype=LT -i}
Humidity: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=HM}
Wind: ${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=WS -i}
${alignr}${voffset -58}${offset -70}${font weather:size=45}${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --datatype=WF}$font
${voffset 15}${color ffffff}3 day forecast
${voffset 7}${color #B3B3B3}${offset 13}${execi 3600 python /home/justin/.scripts/conkyForecast.py -w --location=08628 --startday=1 --endday=4 --datatype=DW --spaces=7}
${font weather:size=33}${offset 6}${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 --startday=1 --endday=4 --datatype=WF} $font
${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=1 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=1 --datatype=LT -i} ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=2 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=2 --datatype=LT -i} ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=3 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=3 --datatype=LT -i} ${execi 3600 python /home/justin/.scripts/conkyForecast.py --startday=4 --location=08628 --datatype=HT -i}/${execi 3600 python /home/justin/.scripts/conkyForecast.py --location=08628 -n --startday=4 --datatype=LT -i}
```

---

### Post by DShroud on 2008-05-22
Wow, awesome post!  Thanks guys, I'll look into making a template for this setup.

EDIT:  Ok, after loading the new .conkyrc that you posted for me, my current processes no longer line up correctly...

[[IMG]http://img508.imageshack.us/img508/6228/conky2db7.th.png[/IMG]](http://img508.imageshack.us/my.php?image=conky2db7.png)

Also, I've made myself a template and it works great, but it doesn't display the weather fonts.  How can I get it to display the weather fonts?

---

### Post by HippyRandall on 2008-05-22
On my machine I had to change [COLOR=Blue]***weather***[/COLOR] to [COLOR=Blue]***Weather***[/COLOR] when using the weather font or the font did not show up properly.
As far as your processes not lining up properly; this was something that I could never get lined up to my satisfaction and I ended up deleting the whole section. Sorry I cant be of more help there.

---

### Post by kaivalagi on 2008-05-22
> **DShroud said:**
> Wow, awesome post!  Thanks guys, I'll look into making a template for this setup.

EDIT:  Ok, after loading the new .conkyrc that you posted for me, my current processes no longer line up correctly...

Also, I've made myself a template and it works great, but it doesn't display the weather fonts.  How can I get it to display the weather fonts?

To display weather fonts you need to have a separate execi call so you can surround it with the conky font settings.

What I have done in the past is had something like this in conkyrc:

```
${color1} ${font Weather:size=48}${execi 1800 python /home/mark/Scripts/conky/conkyForecast.py --location=UKXX0103 --datatype=WF}${font}
${voffset -50}${execi 1800 python /home/mark/Scripts/conky/conkyForecast.py --location=UKXX0103 --template=/home/mark/Scripts/conky/conkyForecast.template}
${voffset -100}  ${font Weather:size=48}${execi 1800 python /home/mark/Scripts/conky/conkyForecast.py --location=UKXX0103 --datatype=WF --startday=1 --endday=3 --spaces=0}
```

So line 1 outputs the current conditions weather font, line 2 outputs all the data for today and the 3 day forecast I want, and line 3 outputs the forecast weather font output. Notice the vertical offsets so everything overlaps nicely.

The template contents for this is:

```
         {--datatype=CC}
         Wind: {--datatype=WS --imperial} - {--datatype=WD}
         Humidity: {--datatype=HM}
    {--datatype=HT --hideunits}/{--datatype=LT --hideunits}  Sun: {--datatype=SR} to {--datatype=SS}
         Bar: {--datatype=BR} - {--datatype=BD}
         Moon: {--datatype=MP}

    {--datatype=DW --startday=1 --shortweekday}        {--datatype=DW --startday=2 --shortweekday}         {--datatype=DW --startday=3 --shortweekday}





   {--datatype=HT --startday=1 --hideunits}/{--datatype=LT --startday=1 --hideunits}    {--datatype=HT --startday=2 --hideunits}/{--datatype=LT --startday=2 --hideunits}     {--datatype=HT --startday=3 --hideunits}/{--datatype=LT --startday=3 --hideunits}
```

The spacing to the top left is where the current conditions weather font goes. The big gap towards the bottom of the template is where the weather fonts for the forecast go.

With anything like this you are best using mono spaced fonts, I personally like Liberation Mono...

Personally, I now just output the forecast data in a strip along the top of my desktop, from a single template based call, and don't even use weather fonts anymore :)

Hope that helps

[COLOR="Blue"]P.S. To stop the warning about the use_spacer option when running conky, in your conkyrc change the "use_spacer yes" to be "use_spacer right", the setting changed with the hardy repo version of conky...[/COLOR]

---

### Post by DShroud on 2008-05-22
Well, I got everything working but the alignment of the processes, so I just got rid of them because it didn't matter that much to me.  Here is a screenshot with my .conkyrc and template I used for anyone who's interested...

[[IMG]http://img175.imageshack.us/img175/7275/conky3ra5.th.png[/IMG]](http://img175.imageshack.us/my.php?image=conky3ra5.png)

My .conkyrc

```
override_utf8_locale yes
text_buffer_size 256

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes
xftfont Arial:size=9

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font arial
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 10

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color green}SYSTEM ${hr 2}$color
$nodename $sysname $kernel on $machine

${color green}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${hwmon 0 temp 1}°C
$cpubar
${cpugraph 000000 ffffff}

${color green}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

Linux: ${fs_free_perc /}%   ${fs_bar 6 /}$color
Media: ${fs_free_perc /media/media}%   ${fs_bar 6 /media/media}

${color green}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color green}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}

${color green}WEATHER${hr 2}$color

${color}Location: Torrington, CT

${execi 1800 python /home/justin/.scripts/conkyForecast.py --location=USCT0232 --template=/home/justin/.scripts/conkyTemplate.template}
${voffset -90}${font Weather:size=48}${execi 1800 python /home/justin/.scripts/conkyForecast.py --location=USCT0232 --datatype=WF --startday=1 --endday=4 --spaces=0}
```



And the template I made...
```
Condition: {--datatype=CC}
Temperature: {--datatype=HT --imperial}
Forecast: {--startday=0 --datatype=HT --imperial}/{--startday=0 --datatype=LT --imperial}
Humidity: {--datatype=HM --imperial}
Wind: {--datatype=WS --imperial}

4 day forecast

{-w --startday=1 --endday=4 --datatype=DW --imperial --spaces=13}



{--startday=1 --datatype=HT --imperial}/{-n --startday=1 --datatype=LT --imperial}       {--startday=2 --datatype=HT --imperial}/{-n --startday=2 --datatype=LT --imperial}         {--startday=3 --datatype=HT --imperial}/{-n --startday=3 --datatype=LT --imperial}         {--startday=4 --datatype=HT --imperial}/{-n --startday=4 --datatype=LT --imperial}

```

For whatever reason the current high temperature is giving me N/A at the moment, hopefully that will fix itself later.  :)

I have one question though, how often does the weather script update?  Every conky update interval?

---

### Post by kaivalagi on 2008-05-22
> **DShroud said:**
> 

And the template I made...
```
Condition: {--datatype=CC}
Temperature: {--datatype=HT --imperial}
Forecast: {[COLOR="Red"]--startday=0[/COLOR] --datatype=HT --imperial}/{[COLOR="Red"]--startday=0[/COLOR] --datatype=LT --imperial}
Humidity: {--datatype=HM --imperial}
Wind: {--datatype=WS --imperial}

4 day forecast

{-w --startday=1 --endday=4 --datatype=DW --imperial --spaces=13}



{--startday=1 --datatype=HT --imperial}/{-n --startday=1 --datatype=LT --imperial}       {--startday=2 --datatype=HT --imperial}/{-n --startday=2 --datatype=LT --imperial}         {--startday=3 --datatype=HT --imperial}/{-n --startday=3 --datatype=LT --imperial}         {--startday=4 --datatype=HT --imperial}/{-n --startday=4 --datatype=LT --imperial}

```

For whatever reason the current high temperature is giving me N/A at the moment, hopefully that will fix itself later.  :)


The reason it is N/A is because after 2pm weather.com make it that way, as it's no longer applicable, current conditions only apply then and not todays forecast. 

_If I were you I would remove the --startday=0 for your today output_. startday=0 is still forecast data, but for today...it enables you to see nighttime weather etc if you use the --night option. 

The LT datatype for current conditions is the feels like temp rather than the low temp...in case you are wondering.

> **DShroud said:**
> 
I have one question though, how often does the weather script update?  Every conky update interval?

Firstly conky will fire the script every interval you set in the execi call. When the script runs it also has an expiry setting which dictates how old the cached data needs to be before a refetch from the weather.com service needs to happen. By default this is 30 minutes. If your execi calls are set to 30+ minutes then that's how regular it will fire _**and**_ update forecast data etc.

---

### Post by HippyRandall on 2008-05-22
can anyone else verify a conflict with the gpanel weather app? it seems to me that any data that conky pulls for itself will not be shown in the panel applet. ie. temps, dew point, humidity. Conky pulls this info but is "Unknown" in the applet. I started up the applet this morning without having run conky all night and it worked fine, and it works fine if I change the location in the applet, but as soon as conky starts up and pulls the info the next update of the applet fails to get this data.

---

### Post by kaivalagi on 2008-05-22
> **HippyRandall said:**
> can anyone else verify a conflict with the gpanel weather app? it seems to me that any data that conky pulls for itself will not be shown in the panel applet. ie. temps, dew point, humidity. Conky pulls this info but is "Unknown" in the applet. I started up the applet this morning without having run conky all night and it worked fine, and it works fine if I change the location in the applet, but as soon as conky starts up and pulls the info the next update of the applet fails to get this data.

I don't even get forecast data for my location in the applet...are you in the US? i.e. could be the NOAA data feed which only has forecast data for the US?

The current conditions from both the applet and the new gnome datetime/weather component are fine

Strange...

[COLOR="Blue"]Edit: Taking a look at the comments in synaptic on the gnome-applets I found this:
[I]Weather report: downloads weather information from the U.S National Weather
Service (NWS) servers, including the Interactive Weather Information
Network (IWIN).
[/I]
At least we know it's not using the same source for weather data as conkyForecast, so it can't be a clash with that...it also explains why I can't get forecast data for the UK! Not good for an international OS really, they should use weather.com like me ;)
[/COLOR]

---

### Post by HippyRandall on 2008-05-22
odd. On the radar tab there is a button to "Visit Weather.com" so I assumed it was pulling all it's data from there.

---

### Post by zeny on 2008-05-22
I've uploaded my template and conkyrc file :)

> # conky configuration
# edited by kaivalagi

# set to yes if you want Conky to be forked in the background
background no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 5x7
#font 6x10
#font 7x13
#font 8x13
#font 9x15
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
#xftfont Bitstream Vera Sans Mono:size=8
#xftfont Terminus:size=8
xftfont Liberation Sans:size=9

# Text alpha when using Xft
xftalpha 0.8

# Print everything to console?
# out_to_console no

# mail spool
#mail_spool $MAIL

# Update interval in seconds
update_interval 5.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 600 5
maximum_width 600

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no
draw_graph_borders yes

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color black
default_outline_color white

# own window options
own_window		yes
own_window_transparent	yes
own_window_type		override
own_window_hints	undecorated,below,sticky,skip_taskbar,skip_pager

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 10
gap_y 0

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# number of cpu samples to average
# set to 1 to disable averaging
cpu_avg_samples 2

# number of net samples to average
# set to 1 to disable averaging
net_avg_samples 2

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

# Add spaces to keep things from moving about?  This only affects certain objects.
use_spacer yes

# colours
color1 white
# light blue
color2 6892C6
# orange
color3 E77320
# green
color4 78BF39
# red
color5 CC0000

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
override_utf8_locale yes
text_buffer_size 256
TEXT



${color2}${font StyleBats:style=CleanCut:size=14}q ${voffset -2}${font Liberation Sans:style=Bold:size=12}Weather${font}   ${hr}

${color1}${font Weather:size=32}${execi 3600 python /home/riban/.scripts/conkyForecast.py --location=CAXX0504 --datatype=WF}${font}
${voffset -40}${execi 3600 python /home/riban/.scripts/conkyForecast.py --location=CAXX0504 --template=/home/riban/.scripts/conkyForecast.template}
${voffset -82}${font Weather:size=32}${execi 3600 python /home/riban/.scripts/conkyForecast.py --location=CAXX0504 --datatype=WF --startday=1 --endday=3 --spaces=0}${font}


>                   {--datatype=CC}
                  Wind: {--datatype=WS --imperial}
                  Humidity: {--datatype=HM}
   {--datatype=HT --hideunits}         Precipitation: {--datatype=PC}

  {--datatype=DW --startday=1 --shortweekday}           {--datatype=DW --startday=2 --shortweekday}            {--datatype=DW --startday=3 --shortweekday}            {--datatype=DW --startday=4 --shortweekday}          



{--datatype=HT --startday=1 --hideunits}/{--datatype=LT --startday=1 --hideunits}       {--datatype=HT --startday=2 --hideunits}/{--datatype=LT --startday=2 --hideunits}       {--datatype=HT --startday=3 --hideunits}/{--datatype=LT --startday=3 --hideunits}   

When I execute that command it works!!

> riban@rOUnz:~/.scripts$ python conkyForecast.py --location=UKXX0103 --template=/home/riban/.scripts/conkyForecast.template
                  Fair
                  Wind: 6mph
                  Humidity: 77%
   12°         Precipitation: N/A

  Fri           Sat            Sun            Mon          



18°/11°       18°/12°       16°/11°   

[email]riban@rOUnz:~/.scri[/email]pts$ 


---

### Post by kaivalagi on 2008-05-23
> **HippyRandall said:**
> odd. On the radar tab there is a button to "Visit Weather.com" so I assumed it was pulling all it's data from there.

The comments in synaptic need updating most probably

I would imagine that both the conky script and the applet use different username/password pairs to retrieve the data from weather.com. The script username/password are register under me...

I'm at a loss...you would think that both forecast and current conditions would be unavailable if there was a weather.com restriction...

---

### Post by kaivalagi on 2008-05-23
> **zeny said:**
> I've uploaded my template and conkyrc file :)

When I execute that command it works!!

No problems using your config etc at this end, with some minor changes to the paths necessary for the scripts and template, it works for me, albeit not quite lined up right. See attached screenshot

Functionally it is fine, if you still have issues check your weather fonts are cached etc (first post instructions)

---

### Post by zeny on 2008-05-23
hmm they should be, I see the first dates weather, maybe my version of conky?

---

### Post by HippyRandall on 2008-05-23
> **kaivalagi said:**
> The comments in synaptic need updating most probably

I would imagine that both the conky script and the applet use different username/password pairs to retrieve the data from weather.com. The script username/password are register under me...

I'm at a loss...you would think that both forecast and current conditions would be unavailable if there was a weather.com restriction...
Well it would seem that it is not related to conky. I haven't had conky running at all today and the applet loaded all the data fine earlier and then it suddenly stopped showing the info that I mentioned earlier. Must be something either with the applet or perhaps the weather station in my area.
:confused:

---

### Post by Apex-jb on 2008-05-25
Is there a way to have it show a moon during the night instead of a sun? Here is my current weather code.

```
${color #0077ff}Weather:
${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CN --refetch}

${color #0077ff}Day: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=DW}
${color #0077ff}Conditions: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=CC}
${font Weather:size=36}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=WF}${font}
${color #0077ff}Temp: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=HT -i}
${color #0077ff}Wind: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=WS -i}
${color #0077ff}Wind Direction: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=WD}
${color #0077ff}Humidity: ${color lightgrey}${execi 3600 python ~/.scripts/conkyForecast.py --location=USIN0707 --datatype=HM}
```
This code is currently showing a sun when it is clear skies even though it is 10:40 at night.

---

### Post by uboops on 2008-05-26
FYI
To show the moon phases ( MF), with the moon_phases.ttf font file:

1) Install the .ttf file
[http://www.dafont.com/moon-phases.font](http://www.dafont.com/moon-phases.font)

2) Add into the .conkyrc file :
${font moon phases:size=37}${execi 3600 python /home/hardy/.conky/conkyForecast.py --location=FRXX0077 --datatype=MF}$font

3) Replace into the conkyForecast.py file, under:

conditions_moon_font = {
		"0": _(u"y"),
		"1": _(u"z"),
		"2": _(u"a"),
		"3": _(u"b"),
		"4": _(u"c"),
		"5": _(u"d"),
		"6": _(u"e"),
		"7": _(u"f"),
		"8": _(u"g"),
		"9": _(u"h"),
		"10": _(u"i"),
		"11": _(u"j"),
		"12": _(u"k"),
		"13": _(u"l"),
		"14": _(u"m"),
		"15": _(u"n"),
		"16": _(u"o"),
		"17": _(u"p"),
		"18": _(u"q"),
		"19": _(u"r"),
		"20": _(u"s"),
		"21": _(u"t"),
		"22": _(u"u"),
		"23": _(u"v"), 
		"24": _(u"w"),
		"25": _(u"x"),
		"na": _(u""),
		"-": _(u"")
	}

---

### Post by Apex-jb on 2008-05-26
> **uboops said:**
> FYI
To show the moon phases ( MF), with the moon_phases.ttf font file:

1) Install the .ttf file
[http://www.dafont.com/moon-phases.font](http://www.dafont.com/moon-phases.font)

2) Add into the .conkyrc file :
${font moon phases:size=37}${execi 3600 python /home/hardy/.conky/conkyForecast.py --location=FRXX0077 --datatype=MF}$font

Thanks, got it working. Now, is there code I can use to make it switch to showing the moon after a certain time of day? Some kind of "if/else" statement?

---

### Post by Bruce M. on 2008-05-26
> **Apex-jb said:**
> Is there a way to have it show a moon during the night instead of a sun? Here is my current weather code.

This code is currently showing a sun when it is clear skies even though it is 10:40 at night.

WoW! Neat idea, but saying that, I would think that would be a programming nightmare. The code would have to check the sunrise and sunset time for each local area and change the font accordingly. And what if it's a "new moon" (blank)?

Nice idea but not "practical" in my opinion.
I may be wrong, I have been wrong before.
Have a nice day, night depending on where you are.
Bruce

---

### Post by kaivalagi on 2008-05-26
> **Apex-jb said:**
> Thanks, got it working. Now, is there code I can use to make it switch to showing the moon after a certain time of day? Some kind of "if/else" statement?

There is no functionality like that you can tweak right now, there is no system time checks to determine what to do.

Feel free to have a dabble...

If you get something working share it and we can get the main py script updated for all to use...

---

### Post by Bruce M. on 2008-05-26
> **uboops said:**
> FYI
To show the moon phases ( MF), with the moon_phases.ttf font file:

1) Install the .ttf file
[http://www.dafont.com/moon-phases.font](http://www.dafont.com/moon-phases.font)

2) Add into the .conkyrc file :
${font moon phases:size=37}${execi 3600 python /home/hardy/.conky/conkyForecast.py --location=FRXX0077 --datatype=MF}$font

3) Replace into the conkyForecast.py file, under:

conditions_moon_font = {
		"0": _(u"y"),
		"1": _(u"z"),
		"2": _(u"a"),
		"3": _(u"b"),
		"4": _(u"c"),
		"5": _(u"d"),
		"6": _(u"e"),
		"7": _(u"f"),
		"8": _(u"g"),
		"9": _(u"h"),
		"10": _(u"i"),
		"11": _(u"j"),
		"12": _(u"k"),
		"13": _(u"l"),
		"14": _(u"m"),
		"15": _(u"n"),
		"16": _(u"o"),
		"17": _(u"p"),
		"18": _(u"q"),
		"19": _(u"r"),
		"20": _(u"s"),
		"21": _(u"t"),
		"22": _(u"u"),
		"23": _(u"v"), 
		"24": _(u"w"),
		"25": _(u"x"),
		"na": _(u""),
		"-": _(u"")
	}

Interesting but where is the "New Moon" and the "Full Moon" 
For me they are missing:

```
	conditions_moon_font = {
		"0": _(u"1"), # Full Moon - see below
		"1": _(u"a"),
		"2": _(u"b"),
		"3": _(u"c"),
		"4": _(u"d"),
		"5": _(u"e"),
		"6": _(u"f"),
		"7": _(u"g"), # First Quarter - see below
		"8": _(u"h"),
		"9": _(u"i"),
		"10": _(u"j"),
		"11": _(u"k"),
		"12": _(u"l"),
		"13": _(u"m"),
		"14": _(u"0"), #New Moon - see below
		"15": _(u"n"),
		"16": _(u"o"),
		"17": _(u"p"),
		"18": _(u"q"),
		"19": _(u"r"),
		"20": _(u"s"),
		"21": _(u"t"), # Last Quarter - see below
		"22": _(u"u"),
		"23": _(u"v"), 
		"24": _(u"w"),
		"25": _(u"x"),
		"26": _(u"y"),
		"27": _(u"z"),
		"na": _(u""),
		"-": _(u"")
	}

```
Which would change the lettering in between, am I wrong in thinking this?

I don't know what adding # 26 and 27 in there will do, but I'm going to test it.

From the MOON.WRI:

> The font depicts the daily phases of the moon for a 28-day lunation.

The new moon is mapped to 0 and *, and the full moon is mapped to @ and is the default for all characters not otherwise occupied (e.g., 1 through 9).

The upper case letters A through Z correspond to the other phases, where A is one day past the new moon (as seen from Earthxs northern hemisphere), G is first quarter, M is one day before the full moon, N is one day past the full moon (remember that the full moon is already assigned to @), T is the last quarter, and Z is one day before the new moon.

I have a feeling this might be slightly different for the southern hemisphere. Not sure.

Have a nice day.
Bruce

---

### Post by Bruce M. on 2008-05-26
First:

[CENTER]**[COLOR="Blue"][SIZE="5"]Thanks uboops for the update![/SIZE][/COLOR]**[/CENTER]

I've applied what uboops said in [post #209]("http://ubuntuforums.org/showpost.php?p=5045197&postcount=209") with the changes mentioned in my previous post (directly above this one), with the exception I'm using CAPS in order to see the entire moon.

I've added #26 & # 27 to accommodate the New Moon and Full Moon. And it seems to be working so far. In order to get it into my "conkymain" I had to redo my conkymain layout.

See attached.

Have a nice Last Quarter.
Bruce

---

### Post by HippyRandall on 2008-05-26
> **Bruce M. said:**
> 
I've applied what uboops said in [post #209]("http://ubuntuforums.org/showpost.php?p=5045197&postcount=209") with the changes mentioned in my previous post (directly above this one), with the exception I'm using CAPS in order to see the entire moon.

I've added #26 & # 27 to accommodate the New Moon and Full Moon. And it seems to be working so far. In order to get it into my "conkymain" I had to redo my conkymain layout.
any chance you could post your setups Bruce? even your conkyForecast.py would be appreciated. I have tried making these changes my self but have not been met with successs. I keep getting N/A rather than a moon font or textual phase. Not real sure what it is I am doing wrong but, like you, I learn best by looking at someone else's code as an example. 
Thanks in advance,
Hippy

---

### Post by Bruce M. on 2008-05-27
> **HippyRandall said:**
> any chance you could post your setups Bruce?
Hippy

Hi Hippy,

Sure not a problem.

First: ~/.startconky
```
#!/bin/bash
sleep 0 &
conky -c ~/Conky/conkymain &
#sleep 0 &
conky -c ~/Conky/conkyforecast &
#sleep 0 &
conky -c ~/Conky/conkyemail &
```
Next: conkymain (top-right)
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
alignment top_right  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
text_buffer_size 128 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

TEXT
${font Zekton:size=11}${color1}${alignc}*** ${color2}GMT$color ${tztime GMT %H:%M} ${color1}***$color$font
${font Zekton:size=11}${alignc}${color2}** ${color1}Canada ${color2}**$color$font
${color1}Winnipeg: $color${tztime Canada/Central %H:%M}${alignr 2}${color1}London${color1}: $color${tztime Canada/Eastern %H:%M}
${color0}${hr 1}$color
${alignc}${color1}--> ${color2}bruloo @ bruloo ${color1}<--$color
${font Zekton:size=20}${alignc}${time %H:%M}$font
${font Zekton:size=12}${color1}${alignc}${time %A, %d %b. %Y}$color$font
${color3}UpTime:${alignr 2}$uptime$color
${color0}${hr 1}$color
${voffset 5}${color2}CPU:${alignc}$color$running_processes ${color1} /$color $processes${alignr 2}${color2}${cpubar cpu0 14,80}$color
${color1}${voffset -16}${alignr 5}$cpu%$color
${voffset 2}${color1}Load Avg (${color3}Min${color1}):${alignr 2}${color3}1: $color${loadavg 1}   ${color3}5: $color${loadavg 2}   ${color3}15: $color${loadavg 3}
${voffset 5}${color2}RAM:$color $mem ${color2} /$color$memmax${alignr 2}${color2}${membar 14,80}$color
${color1}${voffset -16}${alignr 5}$memperc%$color
${voffset 2}${color1}Buffered: $color${buffers}${alignr 2}${color1}Cached:$color ${cached}
${voffset 5}${color2}SWAP: $color$swap ${color2}/ $color${swapmax}${alignr 2}${color2}${swapbar 14,80}$color
${color1}${voffset -16}${alignr 5}$swapperc%
${color0}${hr 1}$color
${voffset 5}${color2}HD Info${color1} -$color Free${color1} - Used - ${color2} Total
${voffset 5}${color1}Root: $color${fs_free_perc /}%${alignr 2}${fs_free /}${color2}/${color1}${fs_used /}$color/${color2}${fs_size /}$color
${color1}Home: $color${fs_free_perc /home/bruloo}%${alignr 2}${fs_free /home/bruloo}${color2}/${color1}${fs_used /home/bruloo}$color/${color2}${fs_size /home/bruloo}$color
${color1}BruLoo: $color${fs_free_perc /media/BruLoo} %${alignr 2}${fs_free /media/BruLoo}${color2}/${color1}${fs_used /media/BruLoo}$color/${color2}${fs_size /media/BruLoo}$color
${color1}40G: $color${fs_free_perc /media/sdb1}%${alignr 2}${fs_free /media/sdb1}${color2}/${color1}${fs_used /media/sdb1}$color/${color2}${fs_size /media/sdb1}$color
${color1}W2K: $color${fs_free_perc /media/sda1}%${alignr 2}${fs_free /media/sda1}${color2}/${color1}${fs_used /media/sda1}$color/${color2}${fs_size /media/sda1}$color
${color0}${hr 1}$color
${color1}Desde:$color Buenos Aires, Argentina
${color1}Lat: ${color2}34°35'S          ${color1}Long: ${color2}58°21'W            ${color1}Alt: ${color2}25 m$color
${voffset 5}${color2}${font Zekton:size=12}hoy:$font ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=CC}$color${alignr 2}${color1}ST: ${color2}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=LT}
${color3}${font Weather:size=50}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=WF}$font$color
${alignr 50}${voffset -55}${font Zekton:size=25}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=HT}$font
${alignc 20}${voffset -30}${font Arrows:size=20}${color4}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=BF}$color$font
${alignc 10}${voffset 5}${color4}Viento: ${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=WS}$color
${color1}Humedad: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=HM}${alignr 2}${color1}Precipitación: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=PC}$color
${alignc}${color1}Presión: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=BR} - ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=BD}$color
${color4}${hr}$color
${color1}Salida del Sol: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=SR}${alignr 2}${color1}Ocaso: ${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=SS}$color
${voffset 15}${color1}Luna:${color4}${alignr 2}${color3}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=MP}$color
${voffset -20}${offset 80}${color4}${font moon phases:size=20}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=MF}$font$color
${color0}${hr}$color
${voffset 5}${color2}IP:${alignc}$color${addr eth0}
${color1}Down: $color${downspeed eth0}k/s ${alignr 2}${color1}Up: $color${upspeed eth0}k/s
${color1}Total: $color${totaldown eth0} ${alignr 2}${color1}Total: $color${totalup eth0} 
${color1}Inbound: $color${tcp_portmon 1 32767 count}          ${color1}Outbound: $color${tcp_portmon 32768 61000 count}${alignr 2}${color1}Total: $color${tcp_portmon 1 65535 count} 
${voffset 5}${color2}Connections: $color${tcp_portmon 32768 61000 count} ${alignr 2} ${color2}Service/Port $color
${voffset 5}${tcp_portmon 32768 61000 rhost 0} ${alignr 2} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr 2} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr 2} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr 2} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr 2} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr 2} ${tcp_portmon 32768 61000 rservice 5}$color
```
Next: conkyforcast (bottom-left) - **only 1 execi call**
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
alignment bottom_left  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

TEXT
${color0}${hr}$color
${color4}${font zekton:size=9}${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --template=/home/bruloo/Conky/scripts/myweather.template}$font$color
```
Next: conkyemail (botton-center) with one test line for "moon", it will be removed
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
alignment bottom_left  # or top_left, bottom_left, bottom_right
gap_x 565
gap_y 35
text_buffer_size 128 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

TEXT
MP: ${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=MP}   MF: ${execi 3600 python ~/Conky/scripts/conkyForecast.py --location=ARBA0009 --datatype=MF}
${color0}${hr}$color
${font Zekton:size=11}${color1}Tenemos  ${color3}${execi 60 python /home/bruloo/Conky/scripts/mail/conkyEmail.py --servertype=POP --servername=pop3.somewhere.com --username=it_is_not_Bruce_M. --password=no_I_will_not_tell_you}${color1}  email(s)$font
```
Next: conkyForecast.py - This one is in Spanish
```
#!/usr/bin/python
# -*- coding: utf-8 -*-
###############################################################################
# conkyForecast.py is a (not so) simple (anymore) python script to gather 
# details of the current weather for use in conky.
#
#  Author: Kaivalagi
# Created: 13/04/2008
# Modifications:
#	14/04/2008	Allow day ranges for forecast data
#	14/04/2008	Check for connectivity to xoap service
#	18/04/2008	Allow the setting of spaces for ranged output
#	18/04/2008	Allow Night and Day forecast output
#	18/04/2008	Support locale for condition code text "CC" option, awaiting spanish language translation
#	18/04/2008	Use pickling for class data rather than opening xml, this bypasses the need to interrogate cached data
#	19/04/2008	Added spanish condition text - Thanks Bruce M
#	19/04/2008	Added isnumeric check on all numeric output with units suffix
#	19/04/2008	Altered pickle file naming to include location code
#	19/04/2008	Added spanish week days conversion via locale
#	20/04/2008	Added decent command argument parser
#	20/04/2008	Added --shortweekday option, if given the day of week data type is shortened to 3 characters
#	21/04/2008	Fixed locale options for forecast output
#	21/04/2008	Added --template option to allow custom output using a single exec call :)
#	21/04/2008	Added --hideunits option to remove, for example, mph and C from output
#	23/04/2008	Removed --imperial option from template, this MUST be set as a standard option on the script call and not used in the template file. 
#	23/04/2008	Readded --imperial option to template, enabling metric or imperial values per datatype. Note when using templates command line option will not work.
#	23/04/2008	Added output notifying user if the location given is bad
#	24/04/2008	Added handling for no connectivity, will revert to cached data now (erroring if no cache exists). Tests by trying to open xoap.weather.com
#	24/04/2008	Fixed Celsius to fahrenheit conversion
#	06/05/2008	Updated url used after webservice was updated
#	09/05/2008	Consolidated current condition and forecast data fetch into one call
#	09/05/2008	Added Sunrise and sunset to datatypes, these are specific to both current conditions and forecast data
#	09/05/2008	Added moon phase, barometer reading and barometer description to datatypes, these are only specific to current conditions and so are N/A in forecasted output
#	09/05/2008	Added unit conversions for barometer from mb to inches (imperial)
#   09/05/2008  Updated spanish condition text - Thanks Bruce M
#   10/05/2008  Added french locale data - Thanks benpaka
#   12/05/2008  Added new BF (bearing font) datatype to provide an arrow character (use with Arrow.ttf font) instead of NSEW output from WD (wind direction)
#   12/05/2008  Updated WD output to be locale specific, currently supports default english and spanish - Thanks Bruce M
#	18/05/2008	Added new MF (moon font) datatype to provide a moon font character (characters incorrect and no dedicated font yet).
#	21/05/2008	For current conditions the --datatype=LT option now displays "feels like" temperature rather than the current temperature
#
# TODO:
# Consolidate pkl files into one file/class
# Add a weather font based moon phase output based on moon icon data
# ??? Any more requirements out there?

import sys, os, socket, urllib2, datetime, time
from xml.dom import minidom
from stat import *
from optparse import OptionParser
import locale
import gettext
import pickle
from math import *

APP="conkyForecast.py"
DIR=os.path.dirname (__file__) + '/locale'
gettext.bindtextdomain(APP, DIR)
gettext.textdomain(APP)
_ = gettext.gettext

class CommandLineParser:

	parser = None

	def __init__(self):

		self.parser = OptionParser()
		self.parser.add_option("-l","--location", dest="location", default="UKXX0103", type="string", metavar="CODE", help=u"location code for weather data [default: %default],Use the following url to determine your location code by city name: http://xoap.weather.com/search/search?where=Norwich")
		self.parser.add_option("-d","--datatype",dest="datatype", default="HT", type="string", metavar="DATATYPE", help=u"[default: %default] The data type options are: DW (Day Of Week), WF (Weather Font Output), LT (Forecast:Low Temp,Current:Feels Like Temp), HT (Forecast:High Temp,Current:Current Temp), CC (Current Conditions), CT (Conditions Text), PC (Precipitation Chance), HM (Humidity), WD (Wind Direction), WS (Wind Speed), WG (Wind Gusts), CN (City Name), SR (sunrise), SS (sunset), MP (moon phase), MF (moon font), BR (barometer reading), BD (barometer description). Not applicable at command line when using templates.")
		self.parser.add_option("-s","--startday",dest="startday", type="int", metavar="NUMBER", help=u"define the starting day number, if omitted current conditions are output. Not applicable at command line when using templates.")
		self.parser.add_option("-e","--endday",dest="endday", type="int", metavar="NUMBER", help=u"define the ending day number, if omitted only starting day data is output. Not applicable at command line when using templates.")
		self.parser.add_option("-S","--spaces",dest="spaces", type="int", default=1, metavar="NUMBER", help=u"[default: %default] Define the number of spaces between ranged output. Not applicable at command line when using templates.")
		self.parser.add_option("-t","--template",dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form {--datatype=HT --startday=1}. The following are possible options within each item: --datatype,--startday,--endday,--night,--shortweekday,--imperial,--hideunits,--spaces . Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
		self.parser.add_option("-L","--locale",dest="locale", type="string", help=u"override the system locale for language output (en=english, es=spanish, fr=french, more to come)")
		self.parser.add_option("-i","--imperial",dest="imperial", default=False, action="store_true", help=u"request imperial units, if omitted output is in metric. Not applicable at command line when using templates.")
		self.parser.add_option("-n","--night",dest="night", default=False, action="store_true", help=u"switch output to night data, if omitted day output will be output. Not applicable at command line when using templates.")
		self.parser.add_option("-w","--shortweekday",dest="shortweekday", default=False, action="store_true", help=u"Shorten the day of week data type to 3 characters. Not applicable at command line when using templates.")
		self.parser.add_option("-u","--hideunits",dest="hideunits", default=False, action="store_true", help=u"Hide units such as mph or C, degree symbols (°) are still shown. Not applicable at command line when using templates.")
		self.parser.add_option("-v","--verbose",dest="verbose", default=False, action="store_true", help=u"request verbose output, no a good idea when running through conky!")
		self.parser.add_option("-r","--refetch",dest="refetch", default=False, action="store_true", help=u"fetch data regardless of data expiry")

	def parse_args(self):
		(options, args) = self.parser.parse_args()
		return (options, args)

	def print_help(self):
		return self.parser.print_help()

class WeatherData:
	def __init__(self, day_of_week, low, high, condition_code, condition_text, precip, humidity, wind_dir, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc):
		self.day_of_week = u""+day_of_week
		self.low = u""+low
		self.high = u""+high
		self.condition_code = u""+condition_code
		self.condition_text = u""+condition_text
		self.precip = u""+precip
		self.humidity = u""+humidity
		self.wind_dir = u""+wind_dir
		self.wind_speed = u""+wind_speed
		self.wind_gusts = u""+wind_gusts
		self.city = u""+city
		self.sunrise = u""+sunrise
		self.sunset = u""+sunset
		self.moon_phase = u""+moon_phase
		self.moon_icon = u""+moon_icon		
		self.bar_read = u""+bar_read
		self.bar_desc = u""+bar_desc


class WeatherText:

	conditions_text = {
		"0": _(u"Tornado"),
		"1": _(u"Tropical Storm"),
		"2": _(u"Hurricane"),
		"3": _(u"Severe Thunderstorms"),
		"4": _(u"Thunderstorms"),
		"5": _(u"Mixed Rain and Snow"),
		"6": _(u"Mixed Rain and Sleet"),
		"7": _(u"Mixed Precipitation"),
		"8": _(u"Freezing Drizzle"),
		"9": _(u"Drizzle"),
		"10": _(u"Freezing Rain"),
		"11": _(u"Showers"),
		"12": _(u"Showers"),
		"13": _(u"Snow Flurries"),
		"14": _(u"Light Snow Showers"),
		"15": _(u"Blowing Snow"),
		"16": _(u"Snow"),
		"17": _(u"Hail"),
		"18": _(u"Sleet"),
		"19": _(u"Dust"),
		"20": _(u"Fog"),
		"21": _(u"Haze"),
		"22": _(u"Smoke"),
		"23": _(u"Blustery"), 
		"24": _(u"Windy"),
		"25": _(u"Cold"),
		"26": _(u"Cloudy"),
		"27": _(u"Mostly Cloudy"),
		"28": _(u"Mostly Cloudy"),
		"29": _(u"Partly Cloudy"),
		"30": _(u"Partly Cloudy"),
		"31": _(u"Clear"),
		"32": _(u"Clear"),
		"33": _(u"Fair"),
		"34": _(u"Fair"),
		"35": _(u"Mixed Rain and Hail"),
		"36": _(u"Hot"),
		"37": _(u"Isolated Thunderstorms"),
		"38": _(u"Scattered Thunderstorms"),
		"39": _(u"Scattered Thunderstorms"),
		"40": _(u"Scattered Showers"),
		"41": _(u"Heavy Snow"),
		"42": _(u"Scattered Snow Showers"),
		"43": _(u"Heavy Snow"),
		"44": _(u"Partly Cloudy"),
		"45": _(u"Thunder Showers"),
		"46": _(u"Snow Showers"),
		"47": _(u"Isolated Thunderstorms"),
		"na": _(u"N/A"),
		"-": _(u"N/A")
	}

	conditions_text_es = {
        "0": _(u"Tornado"),
        "1": _(u"Tormenta Tropical"),
        "2": _(u"Huracá¡n"),
        "3": _(u"Tormentas Fuertes"),
        "4": _(u"Tormentas"),
        "5": _(u"Lluvia y Nieve Mezclada"),
        "6": _(u"Lluvia y Aguanieve Mezclada"),
        "7": _(u"Aguanieve"),
        "8": _(u"Llovizna Helada"),
        "9": _(u"Llovizna"),
        "10": _(u"Lluvia Engelante"), # o lluvia helada
        "11": _(u"Chaparrones"),
        "12": _(u"Chaparrones"),
        "13": _(u"Nieve Ligera"),
        "14": _(u"Nieve Ligera"),
        "15": _(u"Ventisca de Nieve"),
        "16": _(u"Nieve"),
        "17": _(u"Granizo"),
        "18": _(u"Aguanieve"),
        "19": _(u"Polvo"),
        "20": _(u"Niebla"),
        "21": _(u"Bruma"),
        "22": _(u"Humo"),
        "23": _(u"Tempestad"),
        "24": _(u"Ventoso"),
        "25": _(u"Fráo"),
        "26": _(u"Muy Nublado"),
        "27": _(u"Principalmente Nublado"),
        "28": _(u"Principalmente Nublado"),
        "29": _(u"Parcialmente Nublado"),
        "30": _(u"Parcialmente Nublado"),
        "31": _(u"Despejado"),
        "32": _(u"Despejado"),
        "33": _(u"Algo Nublado"),
        "34": _(u"Algo Nublado"),
        "35": _(u"Lluvia con Granizo"),
        "36": _(u"Calor"),
        "37": _(u"Tormentas Aisladas"),
        "38": _(u"Tormentas Dispersas"),
        "39": _(u"Tormentas Dispersas"),
        "40": _(u"Chubascos Dispersos"),
        "41": _(u"Nieve Pesada"),
        "42": _(u"Nevadas Débiles y Dispersas"),
        "43": _(u"Nevada Intensa"),
        "44": _(u"Nubes Dispersas"),
        "45": _(u"Tormentas"),
        "46": _(u"Nevadas Dispersas"),
        "47": _(u"Tormentas Aisladas"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
    }

	conditions_text_fr = {
        "0": _(u"Tornade"),
        "1": _(u"Tempête Tropicale"),
        "2": _(u"Ouragan"),
        "3": _(u"Orages Violents"),
        "4": _(u"Orageux"),
        "5": _(u"Pluie et Neige"),
        "6": _(u"Pluie et Neige Mouillée"),
        "7": _(u"Variable avec averses"),
        "8": _(u"Bruine Givrante"),
        "9": _(u"Bruine"),
        "10": _(u"Pluie Glacante"),
        "11": _(u"Averses"),
        "12": _(u"Averses"),
        "13": _(u"Légère Neige"),
        "14": _(u"Forte Neige"),
        "15": _(u"Tempête de Neige"),
        "16": _(u"Neige"),
        "17": _(u"Grêle"),
        "18": _(u"Pluie/Neige"),
        "19": _(u"Nuage de poussière"),
        "20": _(u"Brouillard"),
        "21": _(u"Brume"),
        "22": _(u"Fumée"),
        "23": _(u"Tres Venteux"),
        "24": _(u"Venteux"),
        "25": _(u"Froid"),
        "26": _(u"Nuageux"),
        "27": _(u"Tres Nuageux"),
        "28": _(u"Tres Nuageux"),
        "29": _(u"Nuages Disséminés"),
        "30": _(u"Nuages Disséminés"),
        "31": _(u"Beau"),
        "32": _(u"Beau"),
        "33": _(u"Belles Éclaircies"),
        "34": _(u"Belles Éclaircies"),
        "35": _(u"Pluie avec Grêle"),
        "36": _(u"Chaleur"),
        "37": _(u"Orages Isolés"),
        "38": _(u"Orages Localisés"),
        "39": _(u"Orages Localisés"),
        "40": _(u"Averses Localisées"),
        "41": _(u"Neige Lourde"),
        "42": _(u"Tempête de Neige Localisées"),
        "43": _(u"Neige Lourde"),
        "44": _(u"Nuages Disséminés"),
        "45": _(u"Orages"),
        "46": _(u"Tempête de Neige"),
        "47": _(u"Orages Isolés"),
        "na": _(u"N/A"),
        "-": _(u"N/A")
	}
	
	conditions_weather_font = {
		"0": _(u"W"),
		"1": _(u"V"),
		"2": _(u"W"),
		"3": _(u"s"),
		"4": _(u"p"),
		"5": _(u"k"),
		"6": _(u"k"),
		"7": _(u"g"),
		"8": _(u"g"),
		"9": _(u"g"),
		"10": _(u"h"),
		"11": _(u"g"),
		"12": _(u"g"),
		"13": _(u"k"),
		"14": _(u"k"),
		"15": _(u"k"),
		"16": _(u"k"),
		"17": _(u"k"),
		"18": _(u"k"),
		"19": _(u"e"),
		"20": _(u"e"),
		"21": _(u"a"),
		"22": _(u"d"),
		"23": _(u"d"), 
		"24": _(u"d"),
		"25": _(u"d"),
		"26": _(u"e"),
		"27": _(u"e"),
		"28": _(u"e"),
		"29": _(u"c"),
		"30": _(u"c"),
		"31": _(u"a"),
		"32": _(u"a"),
		"33": _(u"b"),
		"34": _(u"b"),
		"35": _(u"k"),
		"36": _(u"a"),
		"37": _(u"f"),
		"38": _(u"f"),
		"39": _(u"f"),
		"40": _(u"g"),
		"41": _(u"k"),
		"42": _(u"k"),
		"43": _(u"k"),
		"44": _(u"b"),
		"45": _(u"g"),
		"46": _(u"k"),
		"47": _(u"f"),
		"na": _(u""),
		"-": _(u"")
	}

	conditions_moon_font = {
		"0": _(u"1"),
		"1": _(u"A"),
		"2": _(u"B"),
		"3": _(u"C"),
		"4": _(u"D"),
		"5": _(u"E"),
		"6": _(u"F"),
		"7": _(u"G"),
		"8": _(u"H"),
		"9": _(u"I"),
		"10": _(u"J"),
		"11": _(u"K"),
		"12": _(u"L"),
		"13": _(u"M"),
		"14": _(u"0"),
		"15": _(u"N"),
		"16": _(u"O"),
		"17": _(u"P"),
		"18": _(u"Q"),
		"19": _(u"R"),
		"20": _(u"S"),
		"21": _(u"T"),
		"22": _(u"U"),
		"23": _(u"V"),
		"24": _(u"W"),
		"25": _(u"X"),
		"26": _(u"Y"),
		"27": _(u"Z"),
		"na": _(u""),
		"-": _(u"")
	}
		
	day_of_week = {
		"Today": _(u"Today"),
		"Monday": _(u"Monday"),
		"Tuesday": _(u"Tuesday"),
		"Wednesday": _(u"Wednesday"),
		"Thursday": _(u"Thursday"),
		"Friday": _(u"Friday"),
		"Saturday": _(u"Saturday"),
		"Sunday": _(u"Sunday")
	}

	day_of_week_short = {
		"Today": _(u"Now"),
		"Monday": _(u"Mon"),
		"Tuesday": _(u"Tue"),
		"Wednesday": _(u"Wed"),
		"Thursday": _(u"Thu"),
		"Friday": _(u"Fri"),
		"Saturday": _(u"Sat"),
		"Sunday": _(u"Sun")
	}

	day_of_week_es = {
		"Today": _(u"hoy"),
		"Monday": _(u"lunes"),
		"Tuesday": _(u"martes"),
		"Wednesday": _(u"miércoles"),
		"Thursday": _(u"jueves"),
		"Friday": _(u"viernes"),
		"Saturday": _(u"sábado"),
		"Sunday": _(u"domingo")
	}

	day_of_week_short_es = {
		"Today": _(u"hoy"),
		"Monday": _(u"lun"),
		"Tuesday": _(u"mar"),
		"Wednesday": _(u"mié"),
		"Thursday": _(u"jue"),
		"Friday": _(u"vie"),
		"Saturday": _(u"sáb"),
		"Sunday": _(u"dom")
	}

	day_of_week_fr = {
		"Today": _(u"Aujourd'hui"),
		"Monday": _(u"Lundi"),
		"Tuesday": _(u"Mardi"),
		"Wednesday": _(u"Mercredi"),
		"Thursday": _(u"Jeudi"),
		"Friday": _(u"Vendredi"),
		"Saturday": _(u"Samedi"),
		"Sunday": _(u"Dimanche")
	}

	day_of_week_short_fr = {
		"Today": _(u"Auj"),
		"Monday": _(u"Lun"),
		"Tuesday": _(u"Mar"),
		"Wednesday": _(u"Mer"),
		"Thursday": _(u"Jeu"),
		"Friday": _(u"Ven"),
		"Saturday": _(u"Sam"),
		"Sunday": _(u"Dim")
	}

	bearing_arrow_font = {
		"N": _(u"a"),
		"NNE": _(u"b"),
		"NE": _(u"c"),
		"ENE": _(u"d"),
		"E": _(u"e"),
		"ESE": _(u"f"),
		"SE": _(u"g"),
		"SSE": _(u"h"),
		"S": _(u"i"),
		"SSW": _(u"j"),
		"SW": _(u"k"),
		"WSW": _(u"l"),
		"W": _(u"m"),
		"WNW": _(u"n"),
		"NW": _(u"o"),
		"NNW": _(u"p"),
		"N/A": _(u" ")
	}

	bearing_text_es = {
		"N": _(u"N"),
		"NNE": _(u"NNE"),
		"NE": _(u"NE"),
		"ENE": _(u"ENE"),
		"E": _(u"E"),
		"ESE": _(u"ESE"),
		"SE": _(u"SE"),
		"SSE": _(u"SSE"),
		"S": _(u"S"),
		"SSW": _(u"SSO"),
		"SW": _(u"SO"),
		"WSW": _(u"WOW"),
		"W": _(u"O"),
		"WNW": _(u"ONO"),
		"NW": _(u"NO"),
		"NNW": _(u"NNO"),
		"N/A": _(u"N\A")
	}

	bearing_text_fr = {
		"N": _(u"N"),
		"NNE": _(u"NNE"),
		"NE": _(u"NE"),
		"ENE": _(u"ENE"),
		"E": _(u"E"),
		"ESE": _(u"ESE"),
		"SE": _(u"SE"),
		"SSE": _(u"SSE"),
		"S": _(u"S"),
		"SSW": _(u"SSO"),
		"SW": _(u"SO"),
		"WSW": _(u"WOW"),
		"W": _(u"O"),
		"WNW": _(u"ONO"),
		"NW": _(u"NO"),
		"NNW": _(u"NNO"),
		"N/A": _(u"N\A")		
	}
			  
class GlobalWeather:

	current_conditions = []
	day_forecast = []
	night_forecast = []

	locale = "en"

	options = None
	weatherxmldoc = ""

 	TEMP_FILEPATH_CURRENT = "/tmp/conkyForecast-c-LOCATION.pkl"
	TEMP_FILEPATH_DAYFORECAST = "/tmp/conkyForecast-df-LOCATION.pkl"
	TEMP_FILEPATH_NIGHTFORECAST = "/tmp/conkyForecast-nf-LOCATION.pkl"
 	EXPIRY_MINUTES = 30
	DEFAULT_SPACING = u" "
		

	def __init__(self,options):

		self.options = options
		
		if self.options.locale == None:
			try:
				#self.locale = locale.getdefaultlocale()[0][0:2]
				self.locale = "es" #uncomment this line to force Spanish locale
				#self.locale = "fr" #uncomment this line to force French locale				
			except:
				print "locale not set"
		else:
			#self.locale = self.options.locale
			self.locale = "es" #uncomment this line to force Spanish locale
			#self.locale = "fr" #uncomment this line to force French locale	

		if self.options.verbose == True:
			print >> sys.stdout, "locale set to ",self.locale

	def getText(self,nodelist):
		rc = ""
		for node in nodelist:
			if node.nodeType == node.TEXT_NODE:
				rc = rc + node.data
		return rc


	def getSpaces(self,spaces):
		string = u""
		if spaces == None:
			string = self.DEFAULT_SPACING
		else:
			for i in range(0, spaces+1):
				string = string + u" "
		return string


	def isNumeric(self,string):
		try:
			dummy = float(string)
			return True
		except:
			return False

	def isConnectionAvailable(self):
		# ensure we can access weather.com's server by opening the url
		try:
			usock = urllib2.urlopen('http://xoap.weather.com')
			usock.close()
			return True
		except:
			return False

	def getBearingText(self,bearing):
		bearing = float(bearing)
		if bearing < 11.25:
			return u"N"
		elif bearing < 33.75:
			return u"NNE"
		elif bearing < 56.25:
			return u"NE"
		elif bearing < 78.75:
			return u"ENE"
		elif bearing < 101.25:
			return u"E"
		elif bearing < 123.75:
			return u"ESE"
		elif bearing < 146.25:
			return u"SE"
		elif bearing < 168.75:
			return u"SSE"
		elif bearing < 191.25:
			return u"S"
		elif bearing < 213.75:
			return u"SSW"
		elif bearing < 236.25:
			return u"SW"
		elif bearing < 258.75:
			return u"WSW"
		elif bearing < 281.25:
			return u"W"
		elif bearing < 303.75:
			return u"WNW"
		elif bearing < 326.25:
			return u"NW"
		elif bearing < 348.75:
			return u"NNW"
		else:
			return "N/A"

	def convertCelsiusToFahrenheit(self,temp):
		return str(int(floor(((float(temp)*9.0)/5.0)+32)))

	def convertKilometresToMiles(self,dist):
		return str(int(floor(float(dist)*0.621371192)))

	def convertMillibarsToInches(self,mb):
		return str(int(floor(float(mb)/33.8582)))

	def getTemplateList(self,template):

		templatelist = []
	
		for template_part in template.split("{"):
			if template_part != "":
				for template_part in template_part.split("}"):
					if template_part != "":
						templatelist.append(u""+template_part)

		return templatelist


	def getOutputText(self,datatype,startday,endday,night,shortweekday,imperial,hideunits,spaces):
		#try:
			output = u""
		
			# define current units for output
			if hideunits == False:
				if imperial == False:
					tempunit = u"°C"
					speedunit = u"kph"
					pressureunit = u"mb"
				else:
					tempunit = u"°F"
					speedunit = u"mph"
					pressureunit = u"in"
			else:
				tempunit = u"°"
				speedunit = u""
				pressureunit = u""

			if startday == None: # current conditions

				if datatype == "DW":
					if self.locale == "es":
						if shortweekday == True:
							output = WeatherText.day_of_week_short_es[self.current_conditions[0].day_of_week]
						else:
							output = WeatherText.day_of_week_es[self.current_conditions[0].day_of_week]
					elif self.locale == "fr":
						if shortweekday == True:
							output = WeatherText.day_of_week_short_fr[self.current_conditions[0].day_of_week]
						else:
							output = WeatherText.day_of_week_fr[self.current_conditions[0].day_of_week]							
					else:
						if shortweekday == True:
							output = WeatherText.day_of_week_short[self.current_conditions[0].day_of_week]
						else:
							output = WeatherText.day_of_week[self.current_conditions[0].day_of_week]
				elif datatype == "WF": # weather font
					output = WeatherText.conditions_weather_font[self.current_conditions[0].condition_code]
				elif datatype == "LT":
					string = self.current_conditions[0].low
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertCelsiusToFahrenheit(string)
						string = string + tempunit
					output = string
				elif datatype == "HT":
					string = self.current_conditions[0].high
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertCelsiusToFahrenheit(string)
						string = string + tempunit
					output = string
				elif datatype == "CC":
					if self.locale == "es":
						output = WeatherText.conditions_text_es[self.current_conditions[0].condition_code]
					elif self.locale == "fr":
						output = WeatherText.conditions_text_fr[self.current_conditions[0].condition_code]						
					else:
						output = WeatherText.conditions_text[self.current_conditions[0].condition_code] 
				elif datatype == "CT":
					output = self.current_conditions[0].condition_text
				elif datatype == "PC":
					string = self.current_conditions[0].precip
					if self.isNumeric(string) == True:
						string = string + u"%"
					output = string
				elif datatype == "HM":
					string = self.current_conditions[0].humidity
					if self.isNumeric(string) == True:
						string = string + u"%"
					output = string
				elif datatype == "WD":
					string = self.current_conditions[0].wind_dir
					if self.isNumeric(string) == True:
						string = self.getBearingText(string)
						
					if self.locale == "es":
						output = WeatherText.bearing_text_es[string]
					elif self.locale == "fr":
						output = WeatherText.bearing_text_fr[string]
					else:
						output = string
											
				elif datatype == "BF":
					string = self.current_conditions[0].wind_dir
					if self.isNumeric(string) == True:
						string = WeatherText.bearing_arrow_font[self.getBearingText(string)]
					output = string					
				elif datatype == "WS":
					string = self.current_conditions[0].wind_speed
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertKilometresToMiles(string)
						string = string + speedunit
					output = string
				elif datatype == "WG":
					string = self.current_conditions[0].wind_gusts
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertKilometresToMiles(string)
						string = string + speedunit
					output = string
				elif datatype == "CN":
					output = self.current_conditions[0].city
				elif datatype == "SR":
					output = self.current_conditions[0].sunrise
				elif datatype == "SS":
					output = self.current_conditions[0].sunset
				elif datatype == "MP":
					output = self.current_conditions[0].moon_phase
				elif datatype == "MF":
					output = WeatherText.conditions_moon_font[self.current_conditions[0].moon_icon]							
				elif datatype == "BR":
					string = self.current_conditions[0].bar_read
					if self.isNumeric(string) == True:
						if imperial == True:
							string = self.convertMillibarsToInches(string)
						string = string + pressureunit
					output = string
				elif datatype == "BD":
					output = self.current_conditions[0].bar_desc
				else:
					output = "\nERROR:Unknown data type requested"

			else: # forecast data

				if endday == None: # if no endday was set use startday
					endday = startday

				if night == True: # night forecast required

					for day_number in range(startday, endday+1):

						if datatype == "DW":
							if self.locale == "es":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_es[self.night_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_es[self.night_forecast[day_number].day_of_week]
							elif self.locale == "fr":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_fr[self.night_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_fr[self.night_forecast[day_number].day_of_week]
							else:
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short[self.night_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week[self.night_forecast[day_number].day_of_week]
						elif datatype == "WF": # weather font
							output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.night_forecast[day_number].condition_code]
						elif datatype == "LT":
							string = self.night_forecast[day_number].low
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string

						elif datatype == "HT":
							string = self.night_forecast[day_number].high
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CC":
							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_es[self.night_forecast[day_number].condition_code]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_fr[self.night_forecast[day_number].condition_code]
							else:
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text[self.night_forecast[day_number].condition_code]
						elif datatype == "CT":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].condition_text
						elif datatype == "PC":
							string = self.night_forecast[day_number].precip
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "HM":
							string = self.night_forecast[day_number].humidity
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WD":
							string = self.night_forecast[day_number].wind_dir
							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_es[string]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_fr[string]
							else:
								output = output + self.getSpaces(spaces) + string
                            
						elif datatype == "BF":
							output = output + self.getSpaces(spaces) + WeatherText.bearing_arrow_font[self.night_forecast[day_number].wind_dir]
						elif datatype == "WS":
							string = self.night_forecast[day_number].wind_speed
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WG":
							string = self.night_forecast[day_number].wind_gusts
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CN":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].city
						elif datatype == "SR":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].sunrise
						elif datatype == "SS":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].sunset
						elif datatype == "MP":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].moon_phase
						elif datatype == "MF":
							output = output + self.getSpaces(spaces) + WeatherText.conditions_moon_font[self.night_forecast[day_number].moon_icon]
						elif datatype == "BR":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].bar_read
						elif datatype == "BD":
							output = output + self.getSpaces(spaces) + self.night_forecast[day_number].bar_desc
						else:
							output = "\nERROR:Unknown data type requested"
							break

				else: # day forecast wanted

					for day_number in range(startday, endday+1):

						if datatype == "DW":
							if self.locale == "es":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_es[self.day_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_es[self.day_forecast[day_number].day_of_week]
							elif self.locale == "fr":
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short_fr[self.day_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_fr[self.day_forecast[day_number].day_of_week]									
							else:
								if shortweekday == True:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short[self.day_forecast[day_number].day_of_week]
								else:
									output = output + self.getSpaces(spaces) + WeatherText.day_of_week[self.day_forecast[day_number].day_of_week]
						elif datatype == "WF": # weather font
							output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
						elif datatype == "LT":
							string = self.day_forecast[day_number].low
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "HT":
							string = self.day_forecast[day_number].high
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertCelsiusToFahrenheit(string)
								string = string + tempunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CC":
							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_es[self.day_forecast[day_number].condition_code]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text_fr[self.day_forecast[day_number].condition_code]
							else:
								output = output + self.getSpaces(spaces) + WeatherText.conditions_text[self.day_forecast[day_number].condition_code]
						elif datatype == "CT":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].condition_text
						elif datatype == "PC":
							string = self.day_forecast[day_number].precip
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "HM":
							string = self.day_forecast[day_number].humidity
							if self.isNumeric(string) == True:
								string = string + u"%"
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WD":
							string = self.day_forecast[day_number].wind_dir
							
							if self.locale == "es":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_es[string]
							elif self.locale == "fr":
								output = output + self.getSpaces(spaces) + WeatherText.bearing_text_fr[string]
							else:
								output = output + self.getSpaces(spaces) + string	

						elif datatype == "BF":
							output = output + self.getSpaces(spaces) + WeatherText.bearing_arrow_font[self.day_forecast[day_number].wind_dir]
						elif datatype == "WS":
							string = self.day_forecast[day_number].wind_speed
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "WG":
							string = self.day_forecast[day_number].wind_gusts
							if self.isNumeric(string) == True:
								if imperial == True:
									string = self.convertKilometresToMiles(string)
								string = string + speedunit
							output = output + self.getSpaces(spaces) + string
						elif datatype == "CN":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].city
						elif datatype == "SR":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].sunrise
						elif datatype == "SS":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].sunset
						elif datatype == "MP":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].moon_phase
						elif datatype == "MF":
							output = output + self.getSpaces(spaces) + WeatherText.conditions_moon_font[self.day_forecast[day_number].moon_icon]
						elif datatype == "BR":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].bar_read
						elif datatype == "BD":
							output = output + self.getSpaces(spaces) + self.day_forecast[day_number].bar_desc
						else:
							output = u"\nERROR:Unknown data type requested"
							break

			output = u""+output.strip(u" ") # lose leading/trailing spaces
			return output

		#except:
			#print "getOutputText:Unexpected error: ", sys.exc_info()[0]


	def getOutputTextFromTemplate(self,template):
		#try:

			# keys to template data
			DATATYPE_KEY = "--datatype="
			STARTDAY_KEY = "--startday="
			ENDDAY_KEY = "--endday="
			NIGHT_KEY = "--night"
			SHORTWEEKDAY_KEY = "--shortweekday"
			IMPERIAL_KEY = "--imperial"
			HIDEUNITS_KEY = "--hideunits"
			SPACES_KEY = "--spaces="

			output = u""

			optionfound = False

			#load the file
			try:
				fileinput = open(self.options.template)
				template = fileinput.read()
				fileinput.close()
			except:
				output = u"Template file no found!"

			templatelist = self.getTemplateList(template)

			# lets walk through the template list and determine the output for each item found
			for i in range(0,len(templatelist)-1):

				pos = templatelist[i].find(DATATYPE_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(DATATYPE_KEY)
					datatype = templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" ")
				else:
					datatype = None

				pos = templatelist[i].find(STARTDAY_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(STARTDAY_KEY)
					startday = int(templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" "))
				else:
					startday = None

				pos = templatelist[i].find(ENDDAY_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(ENDDAY_KEY)
					endday = int(templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" "))
				else:
					endday = None

				pos = templatelist[i].find(NIGHT_KEY)
				if pos != -1:
					optionfound = True
					night = True
				else:
					night = False

				pos = templatelist[i].find(SHORTWEEKDAY_KEY)
				if pos != -1:
					optionfound = True
					shortweekday = True
				else:
					shortweekday = False

				pos = templatelist[i].find(IMPERIAL_KEY)
				if pos != -1:
					optionfound = True
					imperial = True
				else:
					imperial = False

				pos = templatelist[i].find(HIDEUNITS_KEY)
				if pos != -1:
					optionfound = True
					hideunits = True
				else:
					hideunits = False

				pos = templatelist[i].find(SPACES_KEY)
				if pos != -1:
					optionfound = True
					pos = pos + len(SPACES_KEY)
					spaces = int(templatelist[i][pos:pos+4].strip("}").strip("{").strip("-").strip(" "))
				else:
					spaces = 1

				if optionfound == True:
					templatelist[i] = self.getOutputText(datatype,startday,endday,night,shortweekday,imperial,hideunits,spaces)
					optionfound = False

			# go through the list concatenating the output now that it's been populated
			for item in templatelist:
				output = output + item

			return output

		#except:
			#print "getOutputTextFromTemplate:Unexpected error: ", sys.exc_info()[0]


	def fetchData(self):

		# always fetch metric data, use conversation functions on this data
		file_path_current = self.TEMP_FILEPATH_CURRENT.replace("LOCATION",self.options.location)
		file_path_dayforecast = self.TEMP_FILEPATH_DAYFORECAST.replace("LOCATION",self.options.location)
		file_path_nightforecast = self.TEMP_FILEPATH_NIGHTFORECAST.replace("LOCATION",self.options.location)

		if self.isConnectionAvailable() == False:
			if os.path.exists(file_path_current):
				RefetchData = False
			else: # no connection, no cache, bang!
				print "No internet connection is available and no cached weather data exists."
		elif self.options.refetch == True:
			RefetchData = True
		else:
	 		# does the data need retrieving again?
	 		if os.path.exists(file_path_current):
	 			lastmodDate = time.localtime(os.stat(file_path_current)[ST_MTIME])
				expiryDate = (datetime.datetime.today() - datetime.timedelta(minutes=self.EXPIRY_MINUTES)).timetuple()

				if expiryDate > lastmodDate:
					RefetchData = True
				else:
					RefetchData = False
			else:
				RefetchData = True


                # fetch the current conditions data, either from the website or by 'unpickling'
 		if RefetchData == True:

			# obtain current conditions data from xoap service
			try:

				# http://xoap.weather.com/weather/local/UKXX0103?cc=*&dayf=5&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b

				url = 'http://xoap.weather.com/weather/local/' + self.options.location + '?cc=*&dayf=8&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b&unit=m'
				if self.options.verbose == True:
					print >> sys.stdout, "fetching weather data from ",url

				usock = urllib2.urlopen(url)
				xml = usock.read()
				usock.close()
				self.weatherxmldoc = minidom.parseString(xml)
			except:
				print "fetchData:Unexpected error: ", sys.exc_info()[0]
				print "Unable to contact weather source for current conditions"

			# tell the user if the location is bad...
			found = xml.find("Invalid location provided")
			if found != -1:
				print "Invalid location provided"

			# interrogate weather data, load into class structure and pickle it
			try:

				# prepare weather data lists
				self.current_conditions = []
				self.day_forecast = []
				self.night_forecast = []

				# collect general data
				weather_n = self.weatherxmldoc.documentElement
				location_n = weather_n.getElementsByTagName('loc')[0]
				city_n = location_n.getElementsByTagName('dnam')[0]
				city = self.getText(city_n.childNodes)

				# collect current conditions data
				day_of_week = u"Today"
				precip = u"N/A"
				sunrise_n = location_n.getElementsByTagName('sunr')[0]
				sunrise = self.getText(sunrise_n.childNodes)
				sunset_n = location_n.getElementsByTagName('suns')[0]
				sunset = self.getText(sunset_n.childNodes)
				current_condition_n = weather_n.getElementsByTagName('cc')[0]
				current_desc_n = current_condition_n.getElementsByTagName('t')[0]
				current_desc = self.getText(current_desc_n.childNodes)
				current_code_n = current_condition_n.getElementsByTagName('icon')[0]
				current_code = self.getText(current_code_n.childNodes)
				current_temp_n = current_condition_n.getElementsByTagName('tmp')[0]
				current_temp = self.getText(current_temp_n.childNodes)
				current_temp_feels_n = current_condition_n.getElementsByTagName('flik')[0]
				current_temp_feels = self.getText(current_temp_feels_n.childNodes)
				bar_n = current_condition_n.getElementsByTagName('bar')[0]
				bar_read_n = bar_n.getElementsByTagName('r')[0]
				bar_read = self.getText(bar_read_n.childNodes)
				bar_desc_n = bar_n.getElementsByTagName('d')[0]
				bar_desc = self.getText(bar_desc_n.childNodes)
				wind_n = current_condition_n.getElementsByTagName('wind')[0]
				wind_speed_n = wind_n.getElementsByTagName('s')[0]
				wind_speed = self.getText(wind_speed_n.childNodes)
				wind_gust_n = wind_n.getElementsByTagName('gust')[0]
				wind_gusts = self.getText(wind_gust_n.childNodes)
				wind_dir_n = wind_n.getElementsByTagName('d')[0]
				wind_direction = self.getText(wind_dir_n.childNodes)
				humidity_n = current_condition_n.getElementsByTagName('hmid')[0]
				humidity = self.getText(humidity_n.childNodes)
				moon_n = current_condition_n.getElementsByTagName('moon')[0]
				moon_icon_n = moon_n.getElementsByTagName('icon')[0]
				moon_icon = self.getText(moon_icon_n.childNodes)
				moon_phase_n = moon_n.getElementsByTagName('t')[0]
				moon_phase = self.getText(moon_phase_n.childNodes)
				current_conditions_data = WeatherData(day_of_week, current_temp_feels, current_temp, current_code, current_desc, precip, humidity, wind_direction, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc)
				self.current_conditions.append(current_conditions_data)

				# collect forecast data
				bar_read = u"N/A"
				bar_desc = u"N/A"
				moon_phase = u"N/A"
				moon_icon = u"na"
				forecast_n = weather_n.getElementsByTagName('dayf')[0]
				day_nodes = forecast_n.getElementsByTagName('day')
	
				for day in day_nodes:
					day_of_week = day.getAttribute('t')
					day_of_year = day.getAttribute('dt')
					high_temp_n = day.getElementsByTagName('hi')[0]
					high_temp = self.getText(high_temp_n.childNodes)
					low_temp_n = day.getElementsByTagName('low')[0]
					low_temp = self.getText(low_temp_n.childNodes)

					sunrise_n = day.getElementsByTagName('sunr')[0]
					sunrise = self.getText(sunrise_n.childNodes)
					sunset_n = day.getElementsByTagName('suns')[0]
					sunset = self.getText(sunset_n.childNodes)

					# day forecast specific data
					daytime_n = day.getElementsByTagName('part')[0] # day
					condition_code_n = daytime_n.getElementsByTagName('icon')[0]
					condition_code = self.getText(condition_code_n.childNodes)
					condition_n = daytime_n.getElementsByTagName('t')[0]
					condition = self.getText(condition_n.childNodes)
					precip_n = daytime_n.getElementsByTagName('ppcp')[0]
					precip = self.getText(precip_n.childNodes)
					humidity_n = daytime_n.getElementsByTagName('hmid')[0]
					humidity = self.getText(humidity_n.childNodes)
					wind_n = daytime_n.getElementsByTagName('wind')[0]
					wind_speed_n = wind_n.getElementsByTagName('s')[0]
					wind_speed = self.getText(wind_speed_n.childNodes)
					wind_direction_n = wind_n.getElementsByTagName('t')[0]
					wind_direction = self.getText(wind_direction_n.childNodes)
					wind_gusts_n = wind_n.getElementsByTagName('gust')[0]
					wind_gusts = self.getText(wind_gusts_n.childNodes)
					day_forecast_data = WeatherData(day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc)
					self.day_forecast.append(day_forecast_data) 	

					# night forecast specific data
					daytime_n = day.getElementsByTagName('part')[1] # night
					condition_code_n = daytime_n.getElementsByTagName('icon')[0]
					condition_code = self.getText(condition_code_n.childNodes)
					condition_n = daytime_n.getElementsByTagName('t')[0]
					condition = self.getText(condition_n.childNodes)
					precip_n = daytime_n.getElementsByTagName('ppcp')[0]
					precip = self.getText(precip_n.childNodes)
					humidity_n = daytime_n.getElementsByTagName('hmid')[0]
					humidity = self.getText(humidity_n.childNodes)
					wind_n = daytime_n.getElementsByTagName('wind')[0]
					wind_speed_n = wind_n.getElementsByTagName('s')[0]
					wind_speed = self.getText(wind_speed_n.childNodes)
					wind_direction_n = wind_n.getElementsByTagName('t')[0]
					wind_direction = self.getText(wind_direction_n.childNodes)
					wind_gusts_n = wind_n.getElementsByTagName('gust')[0]
					wind_gusts = self.getText(wind_gusts_n.childNodes)
					night_forecast_data = WeatherData(day_of_week, low_temp, high_temp, condition_code, condition, precip, humidity, wind_direction, wind_speed, wind_gusts, city, sunrise, sunset, moon_phase, moon_icon, bar_read, bar_desc)
					self.night_forecast.append(night_forecast_data) 


				# pickle the data for next time!
				fileoutput = open(file_path_current, 'w')
 				pickle.dump(self.current_conditions,fileoutput)
		 		fileoutput.close()

				fileoutput = open(file_path_dayforecast, 'w')
 				pickle.dump(self.day_forecast,fileoutput)
		 		fileoutput.close()

				fileoutput = open(file_path_nightforecast, 'w')
 				pickle.dump(self.night_forecast,fileoutput)
		 		fileoutput.close()
		
			except:
				print "fetchData:Unexpected error: ", sys.exc_info()[0]
				print "Unable to interrogate the weather data"

		else: # fetch weather data from pickled class files
			if self.options.verbose == True:
				print >> sys.stdout, "fetching weather data from file: ",file_path_current

 			fileinput = open(file_path_current, 'r')
			self.current_conditions = pickle.load(fileinput)
			fileinput.close()

			if self.options.verbose == True:
				print >> sys.stdout, "fetching day forecast data from files: ",file_path_dayforecast, file_path_nightforecast

 			fileinput = open(file_path_dayforecast, 'r')
			self.day_forecast = pickle.load(fileinput)
			fileinput.close()

			if self.options.verbose == True:
				print >> sys.stdout, "fetching day forecast data from files: ",file_path_nightforecast, file_path_nightforecast

 			fileinput = open(file_path_nightforecast, 'r')
			self.night_forecast = pickle.load(fileinput)
			fileinput.close()

	def outputData(self):
		#try:

			if self.options.template != None:

				output = self.getOutputTextFromTemplate(self.options.template)

			else:

				output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)


			print output.encode("utf-8")

		#except:
			#print "outputData:Unexpected error: ", sys.exc_info()[0]

if __name__ == "__main__":

	parser = CommandLineParser()
	(options, args) = parser.parse_args()

	if options.verbose == True:
		print >> sys.stdout, "location:",options.location
		print >> sys.stdout, "imperial:",options.imperial
		print >> sys.stdout, "datatype:",options.datatype
		print >> sys.stdout, "night:",options.night
		print >> sys.stdout, "start day:",options.startday
		print >> sys.stdout, "end day:",options.endday
		print >> sys.stdout, "spaces:",options.spaces
		print >> sys.stdout, "verbose:",options.verbose
		print >> sys.stdout, "refetch:",options.refetch

	# create new global weather object
	weather = GlobalWeather(options)
	weather.fetchData()
	weather.outputData()


```
And last but not least: myweather.template
```
{--datatype=DW --startday=1}:  {--datatype=CC --startday=1}
{--datatype=HT --startday=1} / {--datatype=LT --startday=1}   Viento del {--datatype=WD --startday=1}  a  {--datatype=WS --startday=1}
Humedad: {--datatype=HM --startday=1}          Precipitacion: {--datatype=PC --startday=1}
Salida del Sol: {--datatype=SR --startday=1}   Ocaso: {--datatype=SS --startday=1}
-----------------------------------------------
{--datatype=DW --startday=2}:  {--datatype=CC --startday=2}
{--datatype=HT --startday=2} / {--datatype=LT --startday=2}   Viento del {--datatype=WD --startday=2}  a  {--datatype=WS --startday=2}
Humedad: {--datatype=HM --startday=2}          Precipitacion: {--datatype=PC --startday=2}
Salida del Sol: {--datatype=SR --startday=2}   Ocaso: {--datatype=SS --startday=2}
-----------------------------------------------
{--datatype=DW --startday=3}:  {--datatype=CC --startday=3}
{--datatype=HT --startday=3} / {--datatype=LT --startday=3}   Viento del {--datatype=WD --startday=3}  a  {--datatype=WS --startday=3}
Humedad: {--datatype=HM --startday=3}          Precipitacion: {--datatype=PC --startday=3}
Salida del Sol: {--datatype=SR --startday=3}   Ocaso: {--datatype=SS --startday=3}
-----------------------------------------------
{--datatype=DW --startday=4}:  {--datatype=CC --startday=4}
{--datatype=HT --startday=4} / {--datatype=LT --startday=4}   Viento del {--datatype=WD --startday=4}  a  {--datatype=WS --startday=4}
Humedad: {--datatype=HM --startday=4}          Precipitacion: {--datatype=PC --startday=4}
Salida del Sol: {--datatype=SR --startday=4}   Ocaso: {--datatype=SS --startday=4}
```
There you have it, the complete setup.

And the inevitable screen-shot:

[CENTER][[IMG]http://img138.imageshack.us/img138/7382/3conkysij1.th.jpg[/IMG]](http://img138.imageshack.us/my.php?image=3conkysij1.jpg)[/CENTER]

Enjoy
Have a nice day
Bruce

---

### Post by HippyRandall on 2008-05-27
> **Bruce M. said:**
> Hi Hippy,

Sure not a problem.


Enjoy
Have a nice day
Bruce

Thanks! It turned out that I had the list wrong for the moon fonts and was calling it the wrong way. I must have been tired when I was messing around with it. Got it all working properly now just need to work on some spacing issues.

Hippy

---

### Post by Bruce M. on 2008-05-27
> **HippyRandall said:**
> Thanks! It turned out that I had the list wrong for the moon fonts and was calling it the wrong way. I must have been tired when I was messing around with it. Got it all working properly now just need to work on some spacing issues.

Hippy

Don't worry it happens to the best, and not being one of the best; me too. :guitar:

Glad you have it working.

Have a good one, Bruce

---

### Post by uboops on 2008-05-27
> **Bruce M. said:**
> First:.....

I've applied what uboops said in [post #209]("http://ubuntuforums.org/showpost.php?p=5045197&postcount=209") with the changes mentioned in my previous post (directly above this one), with the exception I'm using CAPS in order to see the entire moon.

I've added #26 & # 27 to accommodate the New Moon and Full Moon. And it seems to be working so far. In order to get it into my "conkymain" I had to redo my conkymain layout.

See attached.

Have a nice Last Quarter.
Bruce

your welcome !
Good idea, it's more accurate to add the #26 & # 27 items
Have a nice Last Quarter too.
Uboops

---

### Post by Bruce M. on 2008-05-27
> **uboops said:**
> your welcome !
Good idea, it's more accurate to add the #26 & # 27 items
Have a nice Last Quarter too.
Uboops

Just noticed that the "text" is still saying "Last Quarter" but the Moon Font has moved on to "U" ... OK this is working just fine.  :)

Now to get this added to kaivalagi "official" PY file  :)

Have a nice day/night
Bruce

---

### Post by chunchengch on 2008-05-28
Sorry first! I do not read all the posts, so maybe someone had asked same question before.

I find the wind direction is totally reversed, for example, the wind comes from west, but the arrow indicates west instead of east, any idea about this? thanks!

[ATTACH]71884[/ATTACH]

---

### Post by jjgomera on 2008-05-28
its truth, thats sections is wrong:

bearing_arrow_font = {
        "N": _(u"a"),
        "NNE": _(u"b"),
        "NE": _(u"c"),
        "ENE": _(u"d"),
        "E": _(u"e"),
        "ESE": _(u"f"),
        "SE": _(u"g"),
        "SSE": _(u"h"),
        "S": _(u"i"),
        "SSW": _(u"j"),
        "SW": _(u"k"),
        "WSW": _(u"l"),
        "W": _(u"m"),
        "WNW": _(u"n"),
        "NW": _(u"o"),
        "NNW": _(u"p"),
        "N/A": _(u" ")
    }

[IMG]http://img90.imageshack.us/img90/6607/pantallazo1de4.png[/IMG]

it must be:

bearing_arrow_font = {
        "N": _(u"i"),
        "NNE": _(u"j"),
        "NE": _(u"k"),
        "ENE": _(u"l"),
        "E": _(u"m"),
        "ESE": _(u"n"),
        "SE": _(u"o"),
        "SSE": _(u"p"),
        "S": _(u"a"),
        "SSW": _(u"b"),
        "SW": _(u"c"),
        "WSW": _(u"d"),
        "W": _(u"e"),
        "WNW": _(u"f"),
        "NW": _(u"g"),
        "NNW": _(u"h"),
        "N/A": _(u" ")
    }

edit: chunchengch, i like you weatherconky :mrgreen:

---

### Post by chunchengch on 2008-05-28
jjgomera,

Thanks a lot! the problem is fixed.


> **jjgomera said:**
> its truth, thats sections is wrong:

bearing_arrow_font = {
        "N": _(u"a"),
        "NNE": _(u"b"),
        "NE": _(u"c"),
        "ENE": _(u"d"),
        "E": _(u"e"),
        "ESE": _(u"f"),
        "SE": _(u"g"),
        "SSE": _(u"h"),
        "S": _(u"i"),
        "SSW": _(u"j"),
        "SW": _(u"k"),
        "WSW": _(u"l"),
        "W": _(u"m"),
        "WNW": _(u"n"),
        "NW": _(u"o"),
        "NNW": _(u"p"),
        "N/A": _(u" ")
    }

[IMG]http://img90.imageshack.us/img90/6607/pantallazo1de4.png[/IMG]

it must be:

bearing_arrow_font = {
        "N": _(u"i"),
        "NNE": _(u"j"),
        "NE": _(u"k"),
        "ENE": _(u"l"),
        "E": _(u"m"),
        "ESE": _(u"n"),
        "SE": _(u"o"),
        "SSE": _(u"p"),
        "S": _(u"a"),
        "SSW": _(u"b"),
        "SW": _(u"c"),
        "WSW": _(u"d"),
        "W": _(u"e"),
        "WNW": _(u"f"),
        "NW": _(u"g"),
        "NNW": _(u"h"),
        "N/A": _(u" ")
    }

edit: chunchengch, i like you weatherconky :mrgreen:

---

### Post by chunchengch on 2008-05-28
> **jjgomera said:**
> 
edit: chunchengch, i like you weatherconky :mrgreen:

Here is the [ATTACH]71887[/ATTACH] for your reference.

---

### Post by jjgomera on 2008-05-28
thanks

i mean its similar to [mine]("http://ubuntuforums.org/showpost.php?p=4958136&postcount=2384") :mrgreen:

---

### Post by chunchengch on 2008-05-28
> **jjgomera said:**
> thanks

i mean its similar to [mine]("http://ubuntuforums.org/showpost.php?p=4958136&postcount=2384") :mrgreen:

I got it from ubuntu.cn, now I know it is created by you, thanks again!:)

---

### Post by Bruce M. on 2008-05-28
> **chunchengch said:**
> Sorry first! I do not read all the posts, so maybe someone had asked same question before.

I find the wind direction is totally reversed, for example, the wind comes from west, but the arrow indicates west instead of east, any idea about this? thanks!

[ATTACH]71884[/ATTACH]

> **jjgomera said:**
> its truth, thats sections:) is wrong:

bearing_arrow_font = {
        "N": _(u"a"),
        "NNE": _(u"b"),
        "NE": _(u"c"),
        "ENE": _(u"d"),
        "E": _(u"e"),
        "ESE": _(u"f"),
        "SE": _(u"g"),
        "SSE": _(u"h"),
        "S": _(u"i"),
        "SSW": _(u"j"),
        "SW": _(u"k"),
        "WSW": _(u"l"),
        "W": _(u"m"),
        "WNW": _(u"n"),
        "NW": _(u"o"),
        "NNW": _(u"p"),
        "N/A": _(u" ")
    }

[IMG]http://img90.imageshack.us/img90/6607/pantallazo1de4.png[/IMG]

it must be:

bearing_arrow_font = {
        "N": _(u"i"),
        "NNE": _(u"j"),
        "NE": _(u"k"),
        "ENE": _(u"l"),
        "E": _(u"m"),
        "ESE": _(u"n"),
        "SE": _(u"o"),
        "SSE": _(u"p"),
        "S": _(u"a"),
        "SSW": _(u"b"),
        "SW": _(u"c"),
        "WSW": _(u"d"),
        "W": _(u"e"),
        "WNW": _(u"f"),
        "NW": _(u"g"),
        "NNW": _(u"h"),
        "N/A": _(u" ")
    }

edit: chunchengch, i like you weatherconky :mrgreen:

[CENTER][COLOR="Red"][SIZE="7"][B]EDIT: I'm Wrong ...
the script is backwards. :)[/B][/SIZE][/COLOR][/CENTER]

[COLOR="Blue"][SIZE="5"][CENTER]NO! The original script is correct.[/CENTER][/SIZE][/COLOR]

**EDIT TO:** [COLOR="Blue"][SIZE="5"]NO! The original script is wrong.[/SIZE][/COLOR]

This part stands as correct:

> **A north wind is a wind that originates in the north and blows south.**

So the ARROW ***points*** "**[COLOR="Red"]South[/COLOR]**" for a [COLOR="Blue"]**North**[/COLOR] wind.

Weather stations report where the wind is coming from, not the direction it is going.

**Changed to:** **Please Folks, change your scripts.** :lolflag:

OK, that's my mistake today, I always allow myself one before I panic.

Does this mean I have to panic now? . . . ¿:confused:¿

Have a nice **West Wind** going **--->** kind of day.
Bruce

---

### Post by jjgomera on 2008-05-28
sorry bruce but i'm not accord

Naturally ---> this arrow go to East, but for wind the reference is origin, no destiny, so really, if i see that in a map, i interpret west origin wind, and that's the info in weather pages

---

### Post by Bruce M. on 2008-05-28
> **jjgomera said:**
> sorry bruce but i'm not accord

Naturally ---> this arrow go to East, but for wind the reference is origin, no destiny, so really, if i see that in a map, i interpret west origin wind, and that's the info in weather pages

You are right, I am wrong, see the edit above.

En français:

Vous êtes correct, j'étiez mal, voyez mon pour éditer en haut.

Have a great day.
Panic time.  :)
Bruce

---

### Post by martynp on 2008-05-30
Hi All,

Been away for a while but noticed the update with the arrows for wind directions.

Could anyone help me to understand this....

The following line in my .conkyrc returns the arrows but I get 2 with a spurious character at the end. (See attached screenshot)

${font Arrows:size=20}${execi 900 python ~/Conky/conkyForecast.py -r --location=UKXX0212 --datatype=WD}$font

Any help greatly appreciated.

Many Thanks

Martyn

---

### Post by jjgomera on 2008-05-30
With that comand: (--datatype=WD) you have wind direction in letters, NSEW, if you want see with arrows font, you may use:
**--datatype=BF**

---

### Post by Bruce M. on 2008-06-02
Is anyone else missing their "moon font" symbol today and getting the error:

```
bruloo@bruloo:~$ cia
bruloo@bruloo:~$ Conky: desktop window (1000003) is subwindow of root window (4e)
Conky: window type - override
Conky: drawing to created window (2400001)
Conky: drawing to double buffer
Conky: desktop window (1000003) is subwindow of root window (4e)
Conky: window type - override
Conky: drawing to created window (2200001)
Conky: desktop window (1000003) is subwindow of root window (4e)
Conky: window type - override
Conky: drawing to created window (2600001)
Conky: drawing to double buffer
Conky: drawing to double buffer
Traceback (most recent call last):
  File "/home/bruloo/Conky/scripts/conkyForecast.py", line 1295, in <module>
    weather.outputData()
  File "/home/bruloo/Conky/scripts/conkyForecast.py", line 1268, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/bruloo/Conky/scripts/conkyForecast.py", line 726, in getOutputText
    output = WeatherText.conditions_moon_font[self.current_conditions[0].moon_icon]
KeyError: u'28'

```

When they start conky manually?

---

### Post by HippyRandall on 2008-06-02
I am not getting the moon font either. I have not tried starting it from a terminal but I would assume I will get the same error.

[COLOR=Blue]Edit:
Just ran it manually. ouput:

[/COLOR]```
Traceback (most recent call last):
  File "/home/hippy/conky/conkyForecast.py", line 1295, in <module>
    weather.outputData()
  File "/home/hippy/conky/conkyForecast.py", line 1268, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/hippy/conky/conkyForecast.py", line 726, in getOutputText
    output = WeatherText.conditions_moon_font[self.current_conditions[0].moon_icon]                            
KeyError: u'28'

```[COLOR=Blue]
[/COLOR]

---

### Post by Bruce M. on 2008-06-02
> **HippyRandall said:**
> I am not getting the moon font either. I have not tried starting it from a terminal but I would assume I will get the same error.

[COLOR=Blue]Edit:
Just ran it manually. ouput:

[/COLOR]```
Traceback (most recent call last):
  File "/home/hippy/conky/conkyForecast.py", line 1295, in <module>
    weather.outputData()
  File "/home/hippy/conky/conkyForecast.py", line 1268, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/hippy/conky/conkyForecast.py", line 726, in getOutputText
    output = WeatherText.conditions_moon_font[self.current_conditions[0].moon_icon]                            
KeyError: u'28'

```[COLOR=Blue]
[/COLOR]

Yea, looks like we'll have to wait and see what "k" says when he gets home.  :)

---

### Post by HippyRandall on 2008-06-02
to me it seems as if we are missing a font call. I don't know about you but I don't have a '28' in my list of moon fonts in the conkyForecast.py I added another line to the conkyForecast.py with the number '28' and the letter 'Z' and it is showing the font again. Wonder what tomorrow will bring?

---

### Post by kaivalagi on 2008-06-03
> **HippyRandall said:**
> to me it seems as if we are missing a font call. I don't know about you but I don't have a '28' in my list of moon fonts in the conkyForecast.py I added another line to the conkyForecast.py with the number '28' and the letter 'Z' and it is showing the font again. Wonder what tomorrow will bring?

Good catch! The script doesn't know what a value of 28 represents...

I think it's best to wait for a couple of days before I upload the moon font and wind arrows updates. First we make sure we have a fully working solution.

Can Bruce/jjgomera please confirm the final moon icon list edits once we are back to the start of the lunar cycle?

---

### Post by HippyRandall on 2008-06-03
okay so today we are getting a '29' error on a "New Moon"
how long is the actual lunar cycle? 
*heads off to google*

[COLOR=Blue]Edit:
google search for lunar cycle yields:

**[B][SIZE=+1][B]1 lunar cycle = 29.53059 days**[/SIZE][/B][/B]

so I guess we wait till tomorrow to see if it goes back to the start of the list or if we have a '30' error. Would this be a "Leap Moon" :D[/COLOR]

---

### Post by Bruce M. on 2008-06-03
Hi Folks,

I'm testing here, I have added a #29 as a 1 - New Moon since that is what the text says.
This will follow through automatically IF there is no day 30.

There shouldn't be since the cycle is 29.5 days (approx)  :)

We'll see tomorrow.

**EDIT:** I think there will be another change in the positioning of the alphabetic lettering as well. I have more research to do before I'm sure though.

---

### Post by Bruce M. on 2008-06-03
> **HippyRandall said:**
> [COLOR=Blue]Would this be a "Leap Moon" :D[/COLOR]

Does the phrase: [Once in a **[COLOR="Blue"]blue[/COLOR]** moon ring]("http://en.wikipedia.org/wiki/Blue_moon") a bell?

:guitar: By the light, of the silvery moon... :guitar:

---

### Post by Bruce M. on 2008-06-03
> **kaivalagi said:**
> Good catch! The script doesn't know what a value of 28 represents...

We do now, see above.  :)

Testing:
```
		"24": _(u"V"),
		"25": _(u"W"),
		"26": _(u"X"),
		"27": _(u"Y"),
		"28": _(u"Z"),
		"29": _(u"1"),
		"na": _(u""),
		"-": _(u"")
	}
```




> **kaivalagi said:**
> I think it's best to wait for a couple of days before I upload the moon font and wind arrows updates. First we make sure we have a fully working solution.

Good call.

> **kaivalagi said:**
> Can Bruce/jjgomera please confirm the final moon icon list edits once we are back to the start of the lunar cycle?

I'm on it, have it up and running as a test. If it hits 30 today or tomorrow, I'll see it.

Have a nice ... what moon is it today?
Bruce

---

### Post by Bruce M. on 2008-06-03
Hi Folks,

And just in case anyone is **still** wondering ...

 ... *I'm using this font for personal use.*

Have a nice day.
Bruce

---

### Post by HippyRandall on 2008-06-03
Bruce,
I am slightly confused about your post with the partial code for '24'-'29'. below is what I have thus far but it is obviously different from yours in some way. I randomly chose '-' for '28' to see if it worked and what it returned. I must admit that I have not read the font readme.

```
    conditions_moon_font = {
        "0": _(u"1"),
        "1": _(u"A"),
        "2": _(u"B"),
        "3": _(u"C"),
        "4": _(u"D"),
        "5": _(u"E"),
        "6": _(u"F"),
        "7": _(u"G"),
        "8": _(u"H"),
        "9": _(u"I"),
        "10": _(u"J"),
        "11": _(u"K"),
        "12": _(u"L"),
        "13": _(u"M"),
        "14": _(u"0"),
        "15": _(u"N"),
        "16": _(u"O"),
        "17": _(u"P"),
        "18": _(u"Q"),
        "19": _(u"R"),
        "20": _(u"S"),
        "21": _(u"T"),
        "22": _(u"U"),
        "23": _(u"V"),
        "24": _(u"W"),
        "25": _(u"X"),
        "26": _(u"Y"),
        "27": _(u"Z"),
        "28": _(u"-"),
        "29": _(u"1"),
        "na": _(u""),
        "-": _(u"")


```

---

### Post by Bruce M. on 2008-06-03
> **HippyRandall said:**
> Bruce,
I am slightly confused about your post with the partial code for '24'-'29'.

From the Moon Phase WRI file:
> The font depicts the daily phases of the moon for a 28-day lunation.

The new moon is mapped to 0 and *, and the full moon is mapped to @ and is the default for all characters not otherwise occupied (e.g., 1 through 9).

The upper case letters A through Z correspond to the other phases, where A is one day past the new moon (as seen from Earthxs northern hemisphere), G is first quarter, M is one day before the full moon, N is one day past the full moon (remember that the full moon is already assigned to @), T is the last quarter, and Z is one day before the new moon.


Lets see if I can clear up my train of thought for you.

When we hit a #14 and 15 representing a Full Moon I added a test line above my email conky showing exactly what is now in my main conky.

I moved the TEST line to my main conky when we hit the error with 28. So it would be directly under the "Moon Font" and the text output.

When the error continued looking for a non-existent 29 I added that. And as the text said FULL MOON, it needed a 1.  The Z is the normal progression as there are also two calls for FULL MOON #14 & 15. [See Post #175]("http://ubuntuforums.org/showpost.php?p=4994144&postcount=175")

```
	conditions_moon_font = {
		"0": _(u"1"), # New Moon
		"1": _(u"A"), # 6 changes between New and First
		"2": _(u"B"),
		"3": _(u"C"),
		"4": _(u"D"),
		"5": _(u"E"),
		"6": _(u"F"),
		"7": _(u"G"), # First Quarter
		"8": _(u"H"), # 6 changes between First and Full
		"9": _(u"I"),
		"10": _(u"J"),
		"11": _(u"K"),
		"12": _(u"L"),
		"13": _(u"M"),
		"14": _(u"0"), # Full Moon
		"15": _(u"0"), # Full Moon
		"16": _(u"N"), # 6 changes between Full and Last
		"17": _(u"O"),
		"18": _(u"P"),
		"19": _(u"Q"),
		"20": _(u"R"),
		"21": _(u"S"),
		"22": _(u"T"), # Last Quarter
		"23": _(u"U"), # 6 changes between last and New
		"24": _(u"V"),
		"25": _(u"W"),
		"26": _(u"X"),
		"27": _(u"Y"),
		"28": _(u"Z"),
		"29": _(u"1"), # New Moon
		"na": _(u""),
		"-": _(u"")
	}
```

See the images - The first one is for 2 June, the 2nd is for 3 June
Above the test line is the "Moon Font" and the "Text" output of my regular conky

The Test line shows the "letter" I have used (Z) and 1 and the same text output as my regular conky

This way I can match the Moon Font to the text output.

My bet is that with the next change from: **29 - New Moon**; we'll see: **1 - New Moon**

**[COLOR="Red"]EDIT:[/COLOR]** That was **[COLOR="Red"]wrong[/COLOR]** it should be (I hope):
My bet is that with the next change from: **29 - New Moon**; we'll see: **A - Waxing Crescent**

---

### Post by HippyRandall on 2008-06-03
> **Bruce M. said:**
> 
        "14": _(u"0"), # Full Moon
        "15": _(u"0"), # Full Moon

this bit was the difference. Thanks

---

### Post by Bruce M. on 2008-06-03
> **HippyRandall said:**
> this bit was the difference. Thanks

OK, but be aware we still are not 100% sure yet.

---

### Post by HippyRandall on 2008-06-03
oh I know but it helps if we are all on the same page. I will get around to checking out the font readme at some point today

---

### Post by Bruce M. on 2008-06-03
> **HippyRandall said:**
> oh I know but it helps if we are all on the same page. I will get around to checking out the font readme at some point today

Hi Hippy,

Talking about the same page. I have a new conky: **moontest**
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 white
alignment top_left  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y 35
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades yes  # shadecolor black

TEXT
00-1 - ${font moon phases}1$font   ${voffset -4}00-1 - ${font moon phases}1$font  ${voffset -4}New Moon

01-A - ${font moon phases}A$font   ${voffset -4}01-N - ${font moon phases}N$font
02-B - ${font moon phases}B$font   ${voffset -4}02-O - ${font moon phases}O$font
03-C - ${font moon phases}C$font   ${voffset -4}03-P - ${font moon phases}P$font
04-D - ${font moon phases}D$font   ${voffset -4}04-Q - ${font moon phases}Q$font
05-E - ${font moon phases}E$font   ${voffset -4}05-R - ${font moon phases}R$font
06-F - ${font moon phases}F$font   ${voffset -4}06-S - ${font moon phases}S$font

07-G - ${font moon phases}G$font   ${voffset -4}07-T - ${font moon phases}T$font  ${voffset -4}First Quarter

08-H - ${font moon phases}H$font   ${voffset -4}08-U - ${font moon phases}U$font
09-I - ${font moon phases}I$font   ${voffset -4}09-V - ${font moon phases}V$font
10-J - ${font moon phases}J$font   ${voffset -4}10-W - ${font moon phases}W$font
11-K - ${font moon phases}K$font   ${voffset -4}11-X - ${font moon phases}X$font
12-L - ${font moon phases}L$font   ${voffset -4}12-Y - ${font moon phases}Y$font
13-M - ${font moon phases}M$font   ${voffset -4}13-Z - ${font moon phases}Z$font

14-0 - ${font moon phases}0$font   ${voffset -4}14-0 - ${font moon phases}0$font  ${voffset -4}Full Moon

15-0 - ${font moon phases}0$font   ${voffset -4}15-0 - ${font moon phases}0$font  ${voffset -4}Full Moon

16-N - ${font moon phases}N$font   ${voffset -4}16-A - ${font moon phases}A$font
17-O - ${font moon phases}O$font   ${voffset -4}17-B - ${font moon phases}B$font
18-P - ${font moon phases}P$font   ${voffset -4}18-C - ${font moon phases}C$font
19-Q - ${font moon phases}Q$font   ${voffset -4}19-D - ${font moon phases}D$font
20-R - ${font moon phases}R$font   ${voffset -4}20-E - ${font moon phases}E$font
21-S - ${font moon phases}S$font   ${voffset -4}21-F - ${font moon phases}F$font

22-T - ${font moon phases}T$font   ${voffset -4}22-G - ${font moon phases}G$font  ${voffset -4}Last Quarter

23-U - ${font moon phases}U$font   ${voffset -4}23-H - ${font moon phases}H$font
24-V - ${font moon phases}V$font   ${voffset -4}24-I - ${font moon phases}I$font
25-W - ${font moon phases}W$font   ${voffset -4}25-J - ${font moon phases}J$font
26-X - ${font moon phases}X$font   ${voffset -4}26-K - ${font moon phases}K$font
27-Y - ${font moon phases}Y$font   ${voffset -4}27-L - ${font moon phases}L$font
28-Z - ${font moon phases}Z$font   ${voffset -4}28-M - ${font moon phases}M$font

29-1 - ${font moon phases}1$font   ${voffset -4}29-1 - ${font moon phases}1$font  ${voffset -4}New Moon







```
**NOTE:** To see it all you'll have leave 5 blank lines at the end.

The column on the left is the output as it exists today in the PY file (well, for you and I as we are on the same page). Notice how the phases of the moon don't match as you go down the left column.

The column on the right shows the moon phases in proper order after I modified the output in my test conky.  It does go against what the moon phase font creator said in his WRI file, but seeing is believing.

What do you think?

I'm going to modify my conkyForecast.py file to reflect the changes. I'm a "tweak to test junky". I'll see what happens after the next change. There should be just a "sliver" of the moon light up for the next change not a sliver of darkness; "A" should be "N".

Have a good one.
Bruce

---

### Post by HippyRandall on 2008-06-03
I must say that the right column looks much better on my dark background...personal preference aside, do we know for sure that there are two calls to '0' at '14 and '15' for a full moon or is this our 'hack' to get around some inconsistency?

[COLOR=Blue]Edit:
answered my own question by reading the included readme file. since the font is for a *28 day lunar cycle* but actual lunar cycle is roughly *29.5 days* we have to throw in an extra call to...well, ***something, anything*** to stay on track.[/COLOR]

---

### Post by Bruce M. on 2008-06-04
> **HippyRandall said:**
> I must say that the right column looks much better on my dark background...personal preference aside, do we know for sure that there are two calls to '0' at '14 and '15' for a full moon or is this our 'hack' to get around some inconsistency?

Yes, we know for sure, from Post #175, where I *was* keeping a day by day note of what was happening;
```
13 - M - Waxing Gibbous   <- 18 May; MP: Waxing Gibbous - MF:13 
14 - "0" - Full Moon      <- 19 May; MP: Full - MF: 14
15 - "0" - Full Moon      <- 20 May; MP: Full - MF: 15 ???

15 - N - Waning Gibbous   <- ? ?
```
It showed that the moon font (MF) had changed but that the moon phase had remained the same.

> **HippyRandall said:**
> [COLOR=Blue]Edit:
answered my own question by reading the included readme file. since the font is for a *28 day lunar cycle* but actual lunar cycle is roughly *29.5 days* we have to throw in an extra call to...well, ***something, anything*** to stay on track.[/COLOR]

And as it's 29**.5** I believe we need the 30th day in there (#29=30 as 0=1). From what I see in my TEST line it's following what my train of thought is. For the next change I expect to see "N" with a little "sliver" of sunlight on the moon font, and it should happen sometime today.  :)

Have a good day
Bruce

---

### Post by kaivalagi on 2008-06-04
> **Bruce M. said:**
> And as it's 29**.5** I believe we need the 30th day in there (#29=30 as 0=1). From what I see in my TEST line it's following what my train of thought is. For the next change I expect to see "N" with a little "sliver" of sunlight on the moon font, and it should happen sometime today.  :)


I have an N here! (GMT+0) :)

Good to go with your changes?

---

### Post by Bruce M. on 2008-06-04
> **kaivalagi said:**
> I have an N here! (GMT+0) :)

Good to go with your changes?

YES SIR! Good to go.  :)
See attached!

**[CENTER]HUSTON WE HAVE IT WORKING![/CENTER]**

---

### Post by kaivalagi on 2008-06-04
**[COLOR="Blue"][SIZE="4"]UPDATE[/SIZE][/COLOR]**

Hi All,

Script updated in the first post, the below updates have taken place:

[LIST]
[*]Arrows reported to be pointing in the wrong direction. Correction provided by jjgomera
[*]Updated moon font (MF) function to cover the whole lunar cycle hopefully. Added (icon number) days #26, #27, #28 and #29 to complete the cycle. Corrections provided by Bruce M/uboops/HippyRandall
[/LIST]

You'll also now find the moon phase font in the fonts.tar.gz so everything needed should be available for download here :)

Any issues just post back your questions, we're a helpful bunch here ;)

---

### Post by Sam Lars on 2008-06-06
I kind of looked over your recent discussion about the moon, but I think I have a different problem.
If I type the code this way, I get an output:
```
 ~/.conkyweather.py --location=USIL0326 --datatype=MF 
P
```

However, if I add a start day, it gives nothing:
```
 ~/.conkyweather.py --location=USIL0326 --datatype=MF --startday=0

```

Up to 5 where the list goes out of range.
Sorry if this is something I should have realized by now.

---

### Post by HippyRandall on 2008-06-06
not 100% sure but I don't think Moon Phase takes a startday argument. I think it defaults to today.

Hippy

---

### Post by Sam Lars on 2008-06-06
In that case, could it be coded to work all week, or is that information not available?
When I find time I might take a look at this if no one else does.  I'd like to put the moon phases under my days of the week along with the weather font, high/low, conditions, and chance of precipitation.

---

### Post by kaivalagi on 2008-06-07
> **Sam Lars said:**
> In that case, could it be coded to work all week, or is that information not available?
When I find time I might take a look at this if no one else does.  I'd like to put the moon phases under my days of the week along with the weather font, high/low, conditions, and chance of precipitation.

Unfortunately moon phases are not available in the forecast data, only in current conditions data. This is a limitation of the weather.com data feed :(

If you open the following url in your browser you will only see moon related data under the current conditions (cc) xml section, and not in the daily forecast (dayf) xml section:

[URL="http://xoap.weather.com/weather/local/UKXX0103?cc=*&dayf=5&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b"]http://xoap.weather.com/weather/local/UKXX0103?cc=*&dayf=5&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b
[/URL]

Moon data is as follows:
```
    
    <moon>
      <icon>4</icon>
      <t>Waxing Crescent</t>
    </moon>

```

Sorry, but we only use what we are given...

---

### Post by Green_Star on 2008-06-07
How can I make my concy window width bigger something like [this]("http://ubuntuforums.org/showpost.php?p=4753267&postcount=5")

my conky width is small and text is not fitting in it. I tried **text_buffer_size 256** by putthing it at top but  no luck. By the way does anyone has full conky config file of above mentioned link? I like that design.

> 
# UBUNTU-CONKY.
text_buffer_size 256
# Update interval in seconds
update_interval 3.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override #try also 'normal' or 'desktop' 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 250 5
maximum_width 250

draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no

use_xft yes
xftalpha 0.9
xftfont Candera:size=8
uppercase no
override_utf8_locale yes
use_spacer no

stippled_borders 3
border_margin 9
border_width 10

# Gap between borders of screen and text
gap_x 10
gap_y 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color1 orange

# Text alignment, other possible values are commented
#alignment top_left
#alignment top_right
alignment bottom_left
#alignment bottom_right

# stuff after 'TEXT' will be formatted on screen

# ${font weather:size=42}${execi 600 ~/.scripts/conky/scripts/conditions.sh}${font}${voffset -10}  ${execi 1200 ~/.scripts/conky/scripts/pogodynka.sh}

#    ${font weather:size=28}x ${font}HDD ${execi 1 ~/.scripts/conky/scripts/hddmonit.sh} °C
#    ${font weather:size=28}z ${font}CPU ${i2c temp 2} °C 
#    ${font weather:size=28}y ${font}FSB ${i2c temp 1} °C
    
#   ${font PizzaDude Bullets:size=16}v${font}   Up. ${upspeed eth0} Kb/s 
#   ${font PizzaDude Bullets:size=16}r${font}   Dow. ${downspeed eth0} Kb/s 

#   ${font PizzaDude Bullets:size=16}M${font}   Wys&#322;. ${totalup eth0} Kb/s
#   ${font PizzaDude Bullets:size=16}S${font}   Pobr. ${totaldown eth0} Kb/s
   
#   ${font StyleBats:size=18}A${font}   CPU:  ${cpu}
#   ${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

#   ${font FreeSans:size=16}@${font}   e-mail:  ${pop3_unseen adres.pop3 login password -i 600}

#   ${font StyleBats:size=18}P${font}   Work:  ${uptime_short}
#   ${font StyleBats:size=18}4${font}   ${time %A %d %B}

#   ${font xspiralmental:size=17}E${font}   ${kernel}
#

TEXT
${voffset 10}${color}3 day forecast
${voffset 6}${color #B3B3B3}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=1 --datatype=DW}${alignc}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=2 --datatype=DW}
${voffset -12}${alignr}${offset 12}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=3 --datatype=DW}	
${font weather:size=40}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=1 --datatype=WF}
${voffset -55}${offset 50}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=2 --datatype=WF}${alignr}${offset -40}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=2 --datatype=WF}$font

${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --startday=1 --location=CAXX0531 --datatype=HT}/${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 -n --startday=1 --datatype=HT}${alignc}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --startday=2 --location=CAXX0531 --datatype=HT}/${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 -n --startday=2 --datatype=HT}
${voffset -15}${alignr}${voffset 4}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --startday=3 --location=CAXX0531 --datatype=HT}/${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 -n --startday=3 --datatype=HT}



---

### Post by kaivalagi on 2008-06-07
> **Green_Star said:**
> How can I make my concy window width bigger something like [this]("http://ubuntuforums.org/showpost.php?p=4753267&postcount=5")

my conky width is small and text is not fitting in it. I tried **text_buffer_size 256** by putthing it at top but  no luck. By the way does anyone has full conky config file of above mentioned link? I like that design.

Any conky specific questions should really be asked in a more general thread like here: [Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865"). Also, for general help have a read of the documentation on the conky website here: [http://conky.sourceforge.net/documentation.html]("http://conky.sourceforge.net/documentation.html")

But in short you need to alter the following setting :)
```
maximum_width 250
```

Cheers

---

### Post by PatrickMoore on 2008-06-07
Im trying to configure my conkyrc file to show my weather forecast for elgin, il

```
background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.3
total_run_times 0
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no
own_window_transparent yes


double_buffer yes
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
minimum_size 256 5
maximum_width 300
default_color d7d7d7
default_shade_color black
default_outline_color black
alignment top_right
gap_x 2
gap_y 10
no_buffers yes
cpu_avg_samples 2
override_utf8_locale yes
uppercase no # set to yes if you want all text to be in uppercase
use_spacer no

TEXT
${font Zekton:style=Bold:pixelsize=24}${alignc}${time %l:%M:%S %p}${font Zekton:size=8}
SYSTEM ${hr 1 }

CPU       ${alignc} ${freq_dyn}MHz / ${acpitempf}F ${alignr}(${cpu cpu1}%)
${cpubar 4 cpu1}
${cpugraph}
RAM ${alignr}$mem / $memmax ($memperc%)
${membar 4}
SWAP ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Processes: ${alignr}$processes ($running_processes running)

Highest CPU $alignr CPU%       MEM%
${top name 1}$alignr${top cpu 1}         ${top mem 1}
${top name 2}$alignr${top cpu 2}         ${top mem 2}
${top name 3}$alignr${top cpu 3}         ${top mem 3}

Load: ${alignr}$loadavg

FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_free /} / ${fs_size /}
${fs_bar 4 /}
Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/storage} / ${fs_size /media/storage}
${fs_bar 4 /media/storage}

NETWORK ${hr 1}${color}

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 24,128} ${alignr}${upspeedgraph eth0 24,128}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

CURRENT CONDITIONS ${hr 1}${color}

${execi 3600 perl ~/scripts/weather.pl 72584 f 1w}
${execi 3600 perl ~/scripts/weather.pl 72584 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl 72584 f t}
${voffset -15}$alignr${offset -60}${font weather:size=32}${execi 3600 perl ~/scripts/weather.pl 72584 f cp}$font
5 DAY FORECAST ${hr 1}${color}

${font weather:size=55}${execi 3600 perl ~/scripts/weather.pl 72584 f 5dp}${font}$color
${voffset -70}${execi 3600 perl ~/scripts/weather.pl 72584 f 5dt}

```

anyone have any ideas?

---

### Post by easybake on 2008-06-07
your weather.com location is USIL0360. Where did you get that perl script from?

---

### Post by HippyRandall on 2008-06-07
the perl thread can be found here: [http://ubuntuforums.org/showthread.php?t=666842](http://ubuntuforums.org/showthread.php?t=666842)

---

### Post by PatrickMoore on 2008-06-07
> **easybake said:**
> your weather.com location is USIL0360. Where did you get that perl script from?


i found it on another post when i was looking up .conkyrc configurations. it matches up prefectly with my computer ill post the full script if you want it. unless i already did haha. 

my only issue is that i am oblivious on how to configure the weather report.

---

### Post by PatrickMoore on 2008-06-07
> **PatrickMoore said:**
> i found it on another post when i was looking up .conkyrc configurations. it matches up prefectly with my computer ill post the full script if you want it. unless i already did haha. 

my only issue is that i am oblivious on how to configure the weather report.


am i able to  enter into my conkyrc file? or do i have to create a new  file for the weather?

---

### Post by HippyRandall on 2008-06-07
> **HippyRandall said:**
> the conky weather perl thread can be found here: [http://ubuntuforums.org/showthread.php?t=666842](http://ubuntuforums.org/showthread.php?t=666842)
I really can't offer any help on the perl script. This thread uses a python script that alows for the use of templates. This greatly cuts down on the number of execi calls which reduces system load.
You can see the first page of this thread for a complete breakdown of the script and download the script and related fonts.

Good luck,
Hippy

---

### Post by Bruce M. on 2008-06-07
> **PatrickMoore said:**
> Im trying to configure my conkyrc file to show my weather forecast for elgin, il

```
${voffset -70}${execi 3600 perl ~/scripts/weather.pl 72584 f 5dt}
```

anyone have any ideas?

You are using an old .PL script that doesn't work any more, grab the Python script from post #1 in this thread and run that.

> **easybake said:**
> your weather.com location is USIL0360. Where did you get that perl script from?

Agreed, but if you are in the US the ZIP code works just as well.

Have a nice day.
Bruce

---

### Post by Green_Star on 2008-06-08
thanks kaivalagi, i will post my problem in other thread which you mentioned. Any way I already have that variable setup but still not working.

---

### Post by kaivalagi on 2008-06-08
> **Green_Star said:**
> thanks kaivalagi, i will post my problem in other thread which you mentioned. Any way I already have that variable setup but still not working.

Did you increase the maximum_width from 250 to something higher? It should be that simple...

---

### Post by Green_Star on 2008-06-08
Yup, I tried with 300, 500 etc, no luck. Any way I will try again.

---

### Post by kaivalagi on 2008-06-08
> **Green_Star said:**
> Yup, I tried with 300, 500 etc, no luck. Any way I will try again.

What happens with varying maximum widths if you also change the alignment from bottom_left to say top_right?

---

### Post by Green_Star on 2008-06-08
Here is my conky configuration and screenshot. In my screenshot you can see my third day forecast image was out of boundary, that means I can display till that point. So at the bottom where I am printing high/log temperatures... those are too close. depending on that you can imagine my width is smaller. 

```

# UBUNTU-CONKY.
text_buffer_size 256
# Update interval in seconds
update_interval 3.0

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override #try also 'normal' or 'desktop' 
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
#minimum_size 250 5
maximum_width 500

draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no

use_xft yes
xftalpha 0.9
xftfont Candera:size=8
uppercase no
override_utf8_locale yes
use_spacer no

stippled_borders 3
border_margin 9
border_width 10

# Gap between borders of screen and text
gap_x 10
gap_y 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey
color1 orange

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# stuff after 'TEXT' will be formatted on screen

# ${font weather:size=42}${execi 600 ~/.scripts/conky/scripts/conditions.sh}${font}${voffset -10}  ${execi 1200 ~/.scripts/conky/scripts/pogodynka.sh}

#    ${font weather:size=28}x ${font}HDD ${execi 1 ~/.scripts/conky/scripts/hddmonit.sh} °C
#    ${font weather:size=28}z ${font}CPU ${i2c temp 2} °C 
#    ${font weather:size=28}y ${font}FSB ${i2c temp 1} °C
    
#   ${font PizzaDude Bullets:size=16}v${font}   Up. ${upspeed eth0} Kb/s 
#   ${font PizzaDude Bullets:size=16}r${font}   Dow. ${downspeed eth0} Kb/s 

#   ${font PizzaDude Bullets:size=16}M${font}   Wys&#322;. ${totalup eth0} Kb/s
#   ${font PizzaDude Bullets:size=16}S${font}   Pobr. ${totaldown eth0} Kb/s
   
#   ${font StyleBats:size=18}A${font}   CPU:  ${cpu}
#   ${font PizzaDude Bullets:size=16}J${font}   $mem / $memmax

#   ${font FreeSans:size=16}@${font}   e-mail:  ${pop3_unseen adres.pop3 login password -i 600}

#   ${font StyleBats:size=18}P${font}   Work:  ${uptime_short}
#   ${font StyleBats:size=18}4${font}   ${time %A %d %B}

#   ${font xspiralmental:size=17}E${font}   ${kernel}
#

TEXT
${voffset 10}${color}3 day forecast
${voffset 6}${color #B3B3B3}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=1 --datatype=DW}${alignc}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=2 --datatype=DW}
${voffset -12}${alignr}${offset 16}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=3 --datatype=DW}	
${font weather:size=40}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=1 --datatype=WF}
${voffset -55}${offset 70}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=2 --datatype=WF}${alignr}${offset -20}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=2 --datatype=WF}$font

${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --startday=1 --location=CAXX0531 --datatype=HT}/${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 -n --startday=1 --datatype=HT}${alignc}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --startday=2 --location=CAXX0531 --datatype=HT}/${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 -n --startday=2 --datatype=HT}
${voffset -15}${alignr}${voffset 4}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --startday=3 --location=CAXX0531 --datatype=HT}/${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 -n --startday=3 --datatype=HT}

asdf${alignc}asdf${alignr}asdf
```

---

### Post by HippyRandall on 2008-06-08
```
# Minimum size of text area
#minimum_size 250 5
maximum_width 500
```
why not change the maximum_width 500 to something like 550?
might solve the cutoff problem.

---

### Post by Bruce M. on 2008-06-08
> **Green_Star said:**
> Here is my conky configuration and screenshot. In my screenshot you can see my third day forecast image was out of boundary, that means I can display till that point. So at the bottom where I am printing high/log temperatures... those are too close. depending on that you can imagine my width is smaller.

Try this:

```
# Minimum size of text area
#minimum_size 250 5
#maximum_width 500
```

I don't use "minimum size of text area" at all.
Have a nice day
Bruce

---

### Post by Green_Star on 2008-06-09
hmm.. it is strange, i tried maximum_width with 250, 500, 600 and even commented out (like Burce said) everytime i got same width. If some one can give me there whole conky config file, that would be great.

---

### Post by jjgomera on 2008-06-09
i dont know why you used this, really very complex statement:

```
{voffset 6}${color #B3B3B3}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=1 --datatype=WF}${alignc}${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=2 --datatype=WF}
${voffset -12}${alignr}**${offset 16}**${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 --startday=3 --datatype=WF}
```
 in bold the reason because cut the last font 16 px

Really all that you can change for this more simple statement:

```
${execi 3600 python ~/.scripts/conky/weather/conkyForecast.py --location=CAXX0531 **--startday=1 --endday=3** --datatype=WF}
```

---

### Post by martynp on 2008-06-11
Hi All,

Been watching the development of this with interest. Just thought I would add my conky screenie for anyone interested.

I am, in fact, running 2 conky scripts with a delay on startup. I am more interested in weather and news than system monitoring as you will see. I AM using a template but there are also quite a number of exec calls to achieve what I want. System performance is not affected in any way with less than 2mb of RAM being used by both instances. The weather in the main bar is my local and the 3 in the second bar are places I am monitoring for particular reasons. I have done it like this so that I can change the monitored stations as and when I need.

My only issues are with consistent lining up of information when using the templates. As day names and other information changes the formatting can be thrown out a bit as the lining up is not dynamic. Hopefully someone with work out how to fix this in the future.

1. The gap between the two separators shows my Audacious track info when playing.

2. Where you see 'Jordy Makes Mark' is a the RSS headline from a UK Weather site.

The only other things I could ever wish for in conky is 'hoverable' links to show the info contained inside the feed headlines and a way of showing a weather satellite image from conky. Neither is possible as far as I am aware. Anyone???

Regards,

Martyn

---

### Post by kaivalagi on 2008-06-11
> **martynp said:**
> 
The only other things I could ever wish for in conky is 'hoverable' links to show the info contained inside the feed headlines and a way of showing a weather satellite image from conky. Neither is possible as far as I am aware. Anyone???

Regards,

Martyn

We need html content rendering!

About a month or so ago and went and asked the developers of conky (via freenode.net #conky channel) whether there was any potential inclusion of html output in conky for the future, the response was not positive. Conky is a basic text renderer fullstop. HTML specs change and the constant updating was not desired for the team.

I have started learning gtk in python, and in the future may (emphasis on may) publish a python based "desktop info app" that can use html for the output formatting (note, it would be an alternative to conky rather than an addition to it). Everything output could then be lined up properly with tables and positions, and rather than fonts for icons we could use images just as you would in a webpage. I think it would have to start off as an empty shell which will just call user scripts to generate the html...one script per process maybe...

I am currently, at an extremely slow pace, looking at transparency in gtk, afterall we want to be able to see the wallpaper behind any app placed on the desktop! Ideally I could do with some help and/or pointers to documentation, anyone out there who has knowledge of this, please PM me!

P.S. Nice formatting by the way, could you attach your conky configs and templates for people to use and abuse?

---

### Post by Bruce M. on 2008-06-11
> **martynp said:**
> Hi All,

Been watching the development of this with interest. Just thought I would add my conky screenie for anyone interested.

WoW! Nice, it's like a weather station. And you've answered a question I've been pondering for w while but hadn't asked. Can one call the weather from two locations at the same time? Since you are doing 4 I guess 2 is no problem.  **Thanks for answering before I asked.**

> **martynp said:**
> I am, in fact, running 2 conky scripts with a delay on startup. I am more interested in weather and news than system monitoring as you will see. I AM using a template but there are also quite a number of exec calls to achieve what I want. System performance is not affected in any way with less than 2mb of RAM being used by both instances. The weather in the main bar is my local and the 3 in the second bar are places I am monitoring for particular reasons. I have done it like this so that I can change the monitored stations as and when I need.

I hope you plan on showing us the scripts, I'd love to get my teeth into them  :)

---

### Post by Bruce M. on 2008-06-11
> **kaivalagi said:**
> We need html content rendering!

YES! That would be nice.

> **kaivalagi said:**
> About a month or so ago and went and asked the developers of conky (via freenode.net #conky channel) whether there was any potential inclusion of html output in conky for the future, the response was not positive. Conky is a basic text renderer fullstop. HTML specs change and the constant updating was not desired for the team.

That's a lame excuse. <B> </B> was replaced with <STRONG> </STRONG>, etc., etc. But One can still use the defunct commands (even the ones for tables). I used to be a webmaster in the 90's and speak with a certain amount of knowledge on the subject. But that is neither here nor there.

> **kaivalagi said:**
> I have started learning gtk in python, and in the future may (emphasis on may) publish a python based "desktop info app" that can use html for the output formatting (note, it would be an alternative to conky rather than an addition to it). Everything output could then be lined up properly with tables and positions, and rather than fonts for icons we could use images just as you would in a webpage. I think it would have to start off as an empty shell which will just call user scripts to generate the html...one script per process maybe..

Well, I don't know what your doing (code wise) but if you ever need a Chief Cook and Bottle Washer, Beta Tester; I'm your man!

CHIMO!
Bruce

---

### Post by martynp on 2008-06-11
Hi,

The idea of the 'desktop info app' is very exciting...... really hope you go for it!

As requested, attached are my configs.... enjoy!


Martyn

---

### Post by kaivalagi on 2008-06-11
> **Bruce M. said:**
> 
Well, I don't know what your doing (code wise) but if you ever need a Chief Cook and Bottle Washer, Beta Tester; I'm your man!


Thanks Bruce, if there is anything worth testing out of all my endeavours, you'll be the first to find out :)

It will be some time away yet! It's just the odd hour at the weekends

Currently I can't see how I will render html on the desktop with a transparency, web pages have a background after all :( 

Any creative help is welcome!

---

### Post by Bruce M. on 2008-06-11
> **martynp said:**
> Hi,

The idea of the 'desktop info app' is very exciting...... really hope you go for it!

As requested, attached are my configs.... enjoy!


Martyn

Yea, it sure does doesn't it.  :)

Thanks Martyn, appreciate it.

---

### Post by Bruce M. on 2008-06-11
> **kaivalagi said:**
> Thanks Bruce, if there is anything worth testing out of all my endeavours, you'll be the first to find out :)

OK, I'm trimming the bottoms of candles now so I have a good supply to burn at both ends.  :)

You don't even need to ask, just send them my way. :popcorn:

> **kaivalagi said:**
> It will be some time away yet! It's just the odd hour at the weekends

I'll have to talk to your boss to see if we can get you a four day weekend, without a loss of pay of course. Three for work, two for your wife and two for this project.  :lolflag:

> **kaivalagi said:**
> Currently I can't see how I will render html on the desktop with a transparency, web pages have a background after all :( 

Any creative help is welcome!

Hmmm, hadn't thought of that. But I'll do some scrambling around. If there is a will, there's a way.

CHIMO!
Bruce

---

### Post by Bruce M. on 2008-06-11
**[CENTER]Thank you martynp[/CENTER]**

I've been "tweaking" again ... and the results are:
[CENTER][[IMG]http://img395.imageshack.us/img395/6816/weatherns3.th.jpg[/IMG]](http://img395.imageshack.us/my.php?image=weatherns3.jpg)
**[COLOR="DarkRed"]I'm nuts![/COLOR]**[/CENTER]

ImageShack resized it, it is supposed to be 1280x1024.  :(

Running 3 conkys and loving it.

The files I have included here are:
[LIST=1]
[*]~/.startconky
[*]~/Conky/conkymain (on the right)
[*]~/Conky/conkyforcast (on the left)
[*]~/Conky/WEB_USE_conkyemail (center bottom - no name or password)
[*]~/Conky/scripts/SP_Forecast.py (Spanish)
[*]~/Conky/scripts/EN_Forecast.py (English)
[*]~/Conky/scripts/mail/conkyEmail.py
[*]~/Conky/scripts/myweather.template
[*]~/Conky/scripts/argentina.template
[*]~/Conky/scripts/otherweather.template
[/LIST]

Also, in my ~/.bashrc file I use these aliases for conky:
```
# my aliases
alias conke='(gedit ~/.startconky ~/Conky/conkymain ~/Conky/conkyforecast ~/Conky/conkyemail ~/Conky/scripts/SP_Forecast.py ~/Conky/scripts/EN_Forecast.py ~/Conky/scripts/mail/conkyEmail.py ~/Conky/scripts/myweather.template ~/Conky/scripts/argentina.template ~/Conky/scripts/otherweather.template &)'
alias cia='killall conky && ./.startconky'
alias killc='killall conky'
alias stc='~/.startconky'
```
that I had to edit after this session of "tweaking". :lolflag:

Enjoy.
Bruce

---

### Post by HippyRandall on 2008-06-12
> **kaivalagi said:**
> Ideally I could do with some help and/or pointers to documentation, anyone out there who has knowledge of this, please PM me!

P.S. Nice formatting by the way, could you attach your conky configs and templates for people to use and abuse?

this sounds great..I have just moved in to a new place and may not be around very much but I am willing to help out where I can. So far, about all I now about the python and tk is ```
from Tkinter import *
```:lolflag:
if there is anything I can do please feel free to PM me here or MSN, GTalk, email....whatever method is best for you.

---

### Post by kaivalagi on 2008-06-13
> **HippyRandall said:**
> this sounds great..I have just moved in to a new place and may not be around very much but I am willing to help out where I can. So far, about all I now about the python and tk is ```
from Tkinter import *
```:lolflag:
if there is anything I can do please feel free to PM me here or MSN, GTalk, email....whatever method is best for you.

Very funny...:)

As with Bruce as soon as I get (if) to a working solution, I'll pass on what I have for you to try out

I am also looking at the use of cairo and custom xml instead of html, but then it really is getting closer to screenlets etc...I wonder if cairo and gtkhtml can work together to render transparencies...

Anyway, I have a working mini app which just displays html content on the desktop background but with it's own background color :( , all hard coded data at the mo, but working - sort of

---

### Post by kaivalagi on 2008-06-15
[COLOR="Blue"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

I've just added some new datatypes to the script, ask and you shall receive :) (if it's possible!)
The datatypes are: **uv index** (--datatype=UI), **uv text** (--datatype=UT) and **dew point** (--datatype=DP)

You can download the updated script, as usual, from the first post.

**NOTE:** You will probably want to delete any cached data by a previous version of the script as it will not contain the required datatype data. You can do this either by running the script using the --refetch option or by deleting the cached data using the following command:

```
rm /tmp/conkyForecast-*
```

The new datatypes are only applicable to current conditions and not forecast data, they will return as N/A for forecast options.

Chimo!

---

### Post by steve101101 on 2008-06-15
i cannot get the weather icons to display. i believe i have followed your directions, but it still doesn't work. attached are my conky files and screenshot

```



# set to yes if you want Conky to be forked in the background
background no
text_buffer_size 256
cpu_avg_samples 2
net_avg_samples 2

out_to_console no

# X font when Xft is disabled, you can pick one with program xfontsel
#font 7x12
#font 6x10
#font 7x13
#font 8x13
#font 7x12
#font *mintsmild.se*
#font -*-*-*-*-*-*-34-*-*-*-*-*-*-*
#font -artwiz-snap-normal-r-normal-*-*-100-*-*-p-*-iso8859-1

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Bitstream Vera Sans Mono:size=8

own_window_transparent no
#own_window_colour hotpink
# Text alpha when using Xft
xftalpha 0.8

#on_bottom yes

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar
own_window_type override

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Minimum size of text area
minimum_size 260 5
maximum_width 260

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Stippled borders?
stippled_borders no

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color white
default_shade_color white
default_outline_color white

# Text alignment, other possible values are commented
#alignment top_left
#minimum_size 10 10
gap_x 15
gap_y 30 #70
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text

# Add spaces to keep things from moving about?  This only affects certain objects.
#use_spacer no

# Subtract file system buffers from used memory?
no_buffers yes

# set to yes if you want all text to be in uppercase
uppercase no

# none, xmms, bmp, audacious, infopipe (default is none)
#xmms_player bmp

# boinc (seti) dir
# seti_dir /opt/seti

# Possible variables to be used:
#
#      Variable         Arguments                  Description                
#  acpiacadapter                     ACPI ac adapter state.                   
#  acpifan                           ACPI fan state                           
#  acpitemp                          ACPI temperature.                        
#  adt746xcpu                        CPU temperature from therm_adt746x       
#  adt746xfan                        Fan speed from therm_adt746x             
#  battery           (num)           Remaining capasity in ACPI or APM        
#                                    battery. ACPI battery number can be      
#                                    given as argument (default is BAT0).     
#  buffers                           Amount of memory buffered                
#  cached                            Amount of memory cached                  
#  color             (color)         Change drawing color to color            
#  cpu                               CPU usage in percents                    
#  cpubar            (height)        Bar that shows CPU usage, height is      
#                                    bar's height in pixels                   
#  downspeed         net             Download speed in kilobytes              
#  downspeedf        net             Download speed in kilobytes with one     
#                                    decimal                                  
#  exec              shell command   Executes a shell command and displays    
#                                    the output in torsmo. warning: this      
#                                    takes a lot more resources than other    
#                                    variables. I'd recommend coding wanted   
#                                    behaviour in C and posting a patch :-).  
#  execi             interval, shell Same as exec but with specific interval. 
#                    command         Interval can't be less than              
#                                    update_interval in configuration.        
#  fs_bar            (height), (fs)  Bar that shows how much space is used on 
#                                    a file system. height is the height in   
#                                    pixels. fs is any file on that file      
#                                    system.                                  
#  fs_free           (fs)            Free space on a file system available    
#                                    for users.                               
#  fs_free_perc      (fs)            Free percentage of space on a file       
#                                    system available for users.              
#  fs_size           (fs)            File system size                         
#  fs_used           (fs)            File system used space                   
#  hr                (height)        Horizontal line, height is the height in 
#                                    pixels                                   
#  i2c               (dev), type, n  I2C sensor from sysfs (Linux 2.6). dev   
#                                    may be omitted if you have only one I2C  
#                                    device. type is either in (or vol)       
#                                    meaning voltage, fan meaning fan or temp 
#                                    meaning temperature. n is number of the  
#                                    sensor. See /sys/bus/i2c/devices/ on     
#                                    your local computer.                     
#  kernel                            Kernel version                           
#  loadavg           (1), (2), (3)   System load average, 1 is for past 1     
#                                    minute, 2 for past 5 minutes and 3 for   
#                                    past 15 minutes.                         
#  machine                           Machine, i686 for example                
#  mails                             Mail count in mail spool. You can use    
#                                    program like fetchmail to get mails from 
#                                    some server using your favourite         
#                                    protocol. See also new_mails.            
#  mem                               Amount of memory in use                  
#  membar            (height)        Bar that shows amount of memory in use   
#  memmax                            Total amount of memory                   
#  memperc                           Percentage of memory in use              
#  new_mails                         Unread mail count in mail spool.         
#  nodename                          Hostname                                 
#  outlinecolor      (color)         Change outline color                     
#  pre_exec          shell command   Executes a shell command one time before 
#                                    torsmo displays anything and puts output 
#                                    as text.                                 
#  processes                         Total processes (sleeping and running)   
#  running_processes                 Running processes (not sleeping),        
#                                    requires Linux 2.6                       
#  shadecolor        (color)         Change shading color                     
#  stippled_hr       (space),        Stippled (dashed) horizontal line        
#                    (height)        
#  swapbar           (height)        Bar that shows amount of swap in use     
#  swap                              Amount of swap in use                    
#  swapmax                           Total amount of swap                     
#  swapperc                          Percentage of swap in use                
#  sysname                           System name, Linux for example           
#  time              (format)        Local time, see man strftime to get more 
#                                    information about format                 
#  totaldown         net             Total download, overflows at 4 GB on     
#                                    Linux with 32-bit arch and there doesn't 
#                                    seem to be a way to know how many times  
#                                    it has already done that before torsmo   
#                                    has started.                             
#  totalup           net             Total upload, this one too, may overflow 
#  updates                           Number of updates (for debugging)        
#  upspeed           net             Upload speed in kilobytes                
#  upspeedf          net             Upload speed in kilobytes with one       
#                                    decimal                                  
#  uptime                            Uptime                                   
#  uptime_short                      Uptime in a shorter format               
#
#  seti_prog                         Seti@home current progress
#  seti_progbar      (height)        Seti@home current progress bar
#  seti_credit                       Seti@hoome total user credit


# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument
#${font Dungeon:style=Bold:pixelsize=10}I can change the font as well
#${font Verdana:size=10}as many times as I choose
#${font Perry:size=10}Including UTF-8,
# stuff after 'TEXT' will be formatted on screen
#${font Grunge:size=16}${time %a  %b  %d}${alignr -25}${time %k:%M}
#old color -  ${color #0077ff}

TEXT

${color white}$sysname $kernel 
${color white}$machine - $nodename 
${color #e9c703}eth0: ${color white}${addr eth0}
${color #e9c703}Total Upload: ${color white}${totaldown eth0}

${voffset -10}${color1}$hr
${color #e9c703}Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.4 GHz
${voffset -7}${color white}$hr $color

${color #e9c703}Core 1: ${color white}${freq 1} MHz $alignc${color white}${cpubar 5, 120 cpu1} ${cpu cpu1}%
${color #e9c703}Core 2: ${color white}${freq 2} MHz $alignc${color white}${cpubar 5, 120 cpu2} ${cpu cpu2}%
${color #e9c703}Core 3: ${color white}${freq 3} MHz $alignc${color white}${cpubar 5, 120 cpu3} ${cpu cpu3}%
${color #e9c703}Core 4: ${color white}${freq 4} MHz $alignc${color white}${cpubar 5, 120 cpu4} ${cpu cpu4}%

${color #e9c703}RAM:        ${color white}4 GB ${color white}${membar 5,120} ${memperc}%

${color #e9c703}Hard Disks:${color white} - Free Space $fs_free


${voffset -10}${color1}$hr
${color #e9c703}News - RSS Feed:
${voffset -7}${color white}$hr $color
${color white}${rss http://rss.news.yahoo.com/rss/topstories 60 item_titles 10}

${color1}$hr
${voffset -3}$alignc${color #e9c703} Current Conditions
${voffset -7}${color white}$hr $color

${execi 3600 python /home/steven/.scripts/conkyForecast.py --location=UKXX0103 --template=/home/steven/.scripts/conkyForecast.template}


${voffset -10}${color1}$hr
${voffset -3}$alignc${color #e9c703} 5 Day Forecast
${voffset -7}${color white}$hr $color

${voffset -10}${color1}$hr
${color #e9c703}System Logs:
${voffset -7}${color white}$hr $color

${color #e9c703}Messages:
$color${execi 10 /usr/bin/tail -n 5 /var/log/messages | cut -c 23-}
${color #e9c703}Security:
$color${execi 10 /usr/bin/tail -n 5 /var/log/auth.log | cut -c 23-}

${voffset -10}${color1}$hr
${color #e9c703}Now Playing:
${voffset -7}${color white}$hr $color

${exec /usr/bin/rhythmbox-client --print-playing}


```

---

### Post by HippyRandall on 2008-06-15
you need to use something similar to this:```


${font Weather:size=30}${color 5b4b4b}${execi 600 python /home/hippy/conky/conkyForecast.py --location=USME0356 --startday=1 --endday=3 --datatype=WF --spaces=3}${font}
```this is what I use.
Just make sure to put the Weather font in your fonts directory.
Hippy

---

### Post by steve101101 on 2008-06-15
still no icons display

---

### Post by steve101101 on 2008-06-15
i got it working. i just programmed all lines myself. Here is what it looks like. I like it.

---

### Post by yiannit on 2008-06-16
i have a question about starday startday=0 is today? then is startday=1 supposed to be the next daY? and so on? also i cant seems to get a 5 day forecast i get this error

Traceback (most recent call last):
  File "/home/yianni/scripts/conkyForecast.py", line 1330, in <module>
    weather.outputData()
  File "/home/yianni/scripts/conkyForecast.py", line 1303, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/yianni/scripts/conkyForecast.py", line 882, in getOutputText
    output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
IndexError: list index out of range

---

### Post by kaivalagi on 2008-06-16
> **yiannit said:**
> i have a question about starday startday=0 is today? then is startday=1 supposed to be the next daY? and so on? also i cant seems to get a 5 day forecast i get this error

Traceback (most recent call last):
  File "/home/yianni/scripts/conkyForecast.py", line 1330, in <module>
    weather.outputData()
  File "/home/yianni/scripts/conkyForecast.py", line 1303, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/yianni/scripts/conkyForecast.py", line 882, in getOutputText
    output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
IndexError: list index out of range

Yep, startday=0 is today, startday=1 is tomorrow etc. Just remember that if you want to get current conditions use no startday option at all.

The error you are receiving is because the maximum number of forecasted days which weather.com give is 4, if you request up to a startday/endday of 5 or more they script won't find that info because it doesn't exist.

This is mentioned in item 2 of the Gotchas section of the first post on the thread:

2) There is a limit to the maximum range for forecasts, the startday and endday options cannot be set greater than 4, otherwise the script breaks...the following are the options to use to get the maximum forecast of high temps (including forecast data for today):
```
--datatype=HT --startday=0 --endday=4
```

Hope that helps :)

---

### Post by yiannit on 2008-06-16
yeah it makes sense thanks alot

 i came up with another problem it seems like my weather isnt refreshing, i logged onto my xp partition then few hours later back onto linux and it shows the same temperature as before while my linux weather shows 66 degress the conky shows 78, im guessing it has something to do with the pkl files, i removed them, then restarted conky and it worked. is there a way for it to refresh without me having to remove those?

---

### Post by kaivalagi on 2008-06-17
> **yiannit said:**
> yeah it makes sense thanks alot

 i came up with another problem it seems like my weather isnt refreshing, i logged onto my xp partition then few hours later back onto linux and it shows the same temperature as before while my linux weather shows 66 degress the conky shows 78, im guessing it has something to do with the pkl files, i removed them, then restarted conky and it worked. is there a way for it to refresh without me having to remove those?

There is an expiry setting in the script, it defaults to 30 minutes, you could reduce it (see first post for details on EXPIRY). Hence it doesn't make sense that after a couple of hours the details are not refreshed for you.

Alternatively you could use the --refetch option in all the script calls which will bypass the expiry and get new data everytime the script is called. You would then be setting the frequency of the refreshes by you execi interval in conky.

---

### Post by yiannit on 2008-06-17
ok thanks for help i'll keep it as is and see if it does it again if it does ill check out the settings, so does the expiry settings override the execi interval then? is there a way to align fridays weather font without having to type each icon by itself? instead of like this

 ${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=DW -i --shortweekday --startday=1 --endday=3 --spaces=4}
   ${font weather:size=30}${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=WF --startday=1 --endday=3}$font
   ${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=HT -i --startday=1 --endday=3 --spaces=3}

---

### Post by Bruce M. on 2008-06-17
@ yiannit

Unfortunately the weather fonts are not "mono" fonts. Each symbol is a different size, the "Sun" for "Sunny" is the smallest and Lightning Storm being one of the biggest.

If someone who knew how to edit fonts could take it and make all of the symbols the same size that would be better, but that I would think is a big task.

---

### Post by kaivalagi on 2008-06-17
> **Bruce M. said:**
> @ yiannit

Unfortunately the weather fonts are not "mono" fonts. Each symbol is a different size, the "Sun" for "Sunny" is the smallest and Lightning Storm being one of the biggest.

If someone who knew how to edit fonts could take it and make all of the symbols the same size that would be better, but that I would think is a big task.

I am tempted, here's what I think is the process to do that:

[LIST]
[*]Take screenshots of each different character from the weather font, at a high font size, against a white background.
[*]Save the screenshots as individual SVG files, all the same size!
[*]Import the SVG's into fontforge (available via apt) for each character used in the original font
[*]Export a ttf!
[/LIST]

Just not sure how you define a mono font in fontforge, maybe all it needs is the same size svg image imported for each character?

Why don't you give it a go yiannit! :)

---

### Post by jjgomera on 2008-06-17
I'd had this problem, its easy change the font with fontforge

i defined constant width for all used sign to max width, 760, and center. Furthermore reduce width for space for better calibration

its isnt a monospace font, but all sign used here have equal width:

      ```
${color white}${font Weather:size=26}spihda${font}
${color white}${font Weather:size=26}aaWjaa${font}
```

---

### Post by yiannit on 2008-06-17
haha if i only knew how :)

---

### Post by Bruce M. on 2008-06-17
> **kaivalagi said:**
> I am tempted, here's what I think is the process to do that:

[LIST]
[*]Take screenshots of each different character from the weather font, at a high font size, against a white background.
[*]Save the screenshots as individual SVG files, all the same size!
[*]Import the SVG's into fontforge (available via apt) for each character used in the original font
[*]Export a ttf!
[/LIST]

Just not sure how you define a mono font in fontforge, maybe all it needs is the same size svg image imported for each character?

Why don't you give it a go yiannit! :)

I can't get my screenshot to take just a certain area. :(
And GIMP doesn't recognize SVG formats.  :(

---

### Post by Bruce M. on 2008-06-17
> **jjgomera said:**
> I'd had this problem, its easy change the font with fontforge

i defined constant width for all used sign to max width, 760, and center. Furthermore reduce width for space for better calibration

its isnt a monospace font, but all sign used here have equal width:

      ```
${color white}${font Weather:size=26}spihda${font}
${color white}${font Weather:size=26}aaWjaa${font}
```

You are a genius. I have fontforge here but for some reason I cannot see the weather font.  :(

Thanks for this.
CHIMO!
Bruce

---

### Post by kaivalagi on 2008-06-17
> **jjgomera said:**
> I'd had this problem, its easy change the font with fontforge

i defined constant width for all used sign to max width, 760, and center. Furthermore reduce width for space for better calibration

its isnt a monospace font, but all sign used here have equal width:

      ```
${color white}${font Weather:size=26}spihda${font}
${color white}${font Weather:size=26}aaWjaa${font}
```

Fantastic, certainly saves on doing all those steps I mentioned :)

Thanks for the font!
[B]
[SIZE="2"][COLOR="Blue"]Edit: just updated the first post to include the new weather font, thanks again jjgomera[/COLOR][/SIZE][/B]

---

### Post by Bruce M. on 2008-06-17
Hi Folks,

jjgomera took the weather font and made all "font images" the same width, which gave me the "tweaking" bug.

Here's the results:

[CENTER][[IMG]http://img391.imageshack.us/img391/7163/screenshotog3.th.gif[/IMG]](http://img391.imageshack.us/my.php?image=screenshotog3.gif)[/CENTER]

Not bad huh! With only 5 execi calls (4 for the weather fonts and 1 for the 4 days of weather output) I have the 4 day forecast down the left side. I took the stuff for Canada out and added just the current temperature for Winnipeg and London in the main conky on the right.

Here is my conkyforecast:
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 black
alignment bottom_left  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y -250 # because of the VOFFSET of 315 to get the weather font up to the day, the -260 brings conky back to the bottom
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?

TEXT
BUENOS AIRES  ${color0}<<<< 4 Días >>>> ${stippled_hr}$color
${color4}${font zekton:size=9}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --template=/home/bruloo/Conky/scripts/myweather.template}$font$color
${voffset -315}${color3}${font Weather:size=50}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=1}$font$color
${voffset 20}${color3}${font Weather:size=50}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=2}$font$color
${voffset 20}${color3}${font Weather:size=50}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=3}$font$color
${voffset 20}${color3}${font Weather:size=50}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=4}$font$color
```
**Note these lines:**
```
alignment bottom_left  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y -250 # because of the VOFFSET of 315 to get the weather font up to the day, the -260 brings conky back to the bottom
text_buffer_size 1024 # use 1024 for the forecast
```
and my "myweather.template"
```
                  {--datatype=DW --startday=1}:  {--datatype=CC --startday=1}
                  {--datatype=HT --startday=1} / {--datatype=LT --startday=1}       Viento:  {--datatype=WD --startday=1}  a  {--datatype=WS --startday=1}
                  Humedad: {--datatype=HM --startday=1}          Precipitacion: {--datatype=PC --startday=1}
                  Salida del Sol: {--datatype=SR --startday=1}   Ocaso: {--datatype=SS --startday=1}
-----------------------------------------------
                  {--datatype=DW --startday=2}:  {--datatype=CC --startday=2}
                  {--datatype=HT --startday=2} / {--datatype=LT --startday=2}       Viento:  {--datatype=WD --startday=2}  a  {--datatype=WS --startday=2}
                  Humedad: {--datatype=HM --startday=2}          Precipitacion: {--datatype=PC --startday=2}
                  Salida del Sol: {--datatype=SR --startday=2}   Ocaso: {--datatype=SS --startday=2}
-----------------------------------------------
                  {--datatype=DW --startday=3}:  {--datatype=CC --startday=3}
                  {--datatype=HT --startday=3} / {--datatype=LT --startday=3}       Viento:  {--datatype=WD --startday=3}  a  {--datatype=WS --startday=3}
                  Humedad: {--datatype=HM --startday=3}          Precipitacion: {--datatype=PC --startday=3}
                  Salida del Sol: {--datatype=SR --startday=3}   Ocaso: {--datatype=SS --startday=3}
-----------------------------------------------
                  {--datatype=DW --startday=4}:  {--datatype=CC --startday=4}
                  {--datatype=HT --startday=4} / {--datatype=LT --startday=4}       Viento:  {--datatype=WD --startday=4}  a  {--datatype=WS --startday=4}
                  Humedad: {--datatype=HM --startday=4}          Precipitacion: {--datatype=PC --startday=4}
                  Salida del Sol: {--datatype=SR --startday=4}   Ocaso: {--datatype=SS --startday=4}
```
[CENTER][SIZE="6"]**Thanks again JJ**[/SIZE][/CENTER]

Have a nice day.
Bruce

---

### Post by puppyguy on 2008-06-18
hi kaivalagi,i am doing something with google map api.i want to  use python script fetches the new weather data from weather.com,then show the weather info on the google map.

just like the site [http://maps.gokulsoundar.com]("http://maps.gokulsoundar.com")

the problem is i know nothing about python,so i find this post by google.i want to ask if i could use conkyForecast.py to create a xml file to use on google map ,how to modify this python script file,this is so hard to me.

i execute  #python conkyForecast.py  in it just create three files in /tmp ,I'm totally confused now.

execuse my poor english.

---

### Post by kaivalagi on 2008-06-18
> **puppyguy said:**
> hi kaivalagi,i am doing something with google map api.i want to  use python script fetches the new weather data from weather.com,then show the weather info on the google map.

just like the site [http://maps.gokulsoundar.com]("http://maps.gokulsoundar.com")

the problem is i know nothing about python,so i find this post by google.i want to ask if i could use conkyForecast.py to create a xml file to use on google map ,how to modify this python script file,this is so hard to me.

i execute  #python conkyForecast.py  in it just create three files in /tmp ,I'm totally confused now.

execuse my poor english.

The 3 files in tmp relate to 'pickled' classes and not strictly the xml from weather.com. They will be of no use to you.

If you want the xml from the weather.com site you need to use this portion of code with varying location codes for each location you want weather data for:

```
#http://xoap.weather.com/weather/local/UKXX0103?cc=*&dayf=5&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b

url = 'http://xoap.weather.com/weather/local/' + self.options.location + '?cc=*&dayf=8&link=xoap&prod=xoap&par=1061785028&key=e374effbfd74930b&unit=m'
usock = urllib2.urlopen(url)
xml = usock.read()
```

You should use your own registration codes for the url, please don't use mine. If you use them as well the chances are the account will get closed and neither of us will be able to recieve data. It is also worth registering for the service as you'll recieve documents on the service and what it provides! Very useful.

Read this post from _this_ thread, all the details you'll need to get started are there :)

[http://ubuntuforums.org/showpost.php?p=4994793&postcount=176]("http://ubuntuforums.org/showpost.php?p=4994793&postcount=176")

Good luck!

P.S. I really don't have time to help you through every step of your python development, that's something you need to figure out for yourself. Both myself and HippyRandall can assist here and there if it's _really_ needed. Please don't abuse our generosity though ;)

---

### Post by yiannit on 2008-06-18
jj that doesnt really help it kinda makes it worse im trying to get the icons aligned without having to have a commmand for each icon with your icon sizes theyre way off alignment

   ${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=DW -i --shortweekday --startday=1 --endday=3 --spaces=4}
   ${font weather:size=30}${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=WF --startday=1 --endday=3 }$font
   ${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=HT -i --startday=1 --endday=3 --spaces=3}

---

### Post by jjgomera on 2008-06-18
> **yiannit said:**
> jj that doesnt really help it kinda makes it worse im trying to get the icons aligned without having to have a commmand for each icon with your icon sizes theyre way off alignment

   ${font weather:size=30}${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=WF --startday=1 --endday=3 **--spaces=5** }$font
play with spaces :)

---

### Post by yiannit on 2008-06-18
i tried when i add --spaces command i still cant get the last icon aligned

---

### Post by Bruce M. on 2008-06-18
> **yiannit said:**
> jj that doesnt really help it kinda makes it worse im trying to get the icons aligned without having to have a commmand for each icon with your icon sizes theyre way off alignment

   ${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=DW -i --shortweekday --startday=1 --endday=3 --spaces=4}
   ${font weather:size=30}${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=WF --startday=1 --endday=3 }$font
   ${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091 --datatype=HT -i --startday=1 --endday=3 --spaces=3}

> **jjgomera said:**
> play with spaces :)

I agree, and also use the ${goto xx} command, it looks good to me.
```
${goto 18}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=DW -i --shortweekday --startday=1 --endday=3 --spaces=6}
${font weather:size=30}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=1 --endday=3 }$font
${goto 12}${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=HT -i --startday=1 --endday=3 --spaces=4}
```

I only changed:
```
${execi 3600 python ~/scripts/conkyForecast.py --location=USOH1091
```
to
```
${execi 600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009
```
to match my system. Added the ${goto xx} and adjusted spaces.

**EDIT:** Be aware that the weather fonts all have the same width, but you may be using a variable width font in your conky as well, this will make things difficult to line them up. Try using a "mono" type font for the weather calls and things should get even more inline.

---

### Post by kaivalagi on 2008-06-18
**[SIZE="4"][COLOR="Blue"]UPDATE (IMPORTANT)[/COLOR][/SIZE]**

I have just updated the script, see the amendments below:

[LIST]
[*]18/06/2008	Updated DP (dew point) output to convert to imperial units when required - thanks HippyRandall
[*]18/06/2008	Added Spanish and French translations for UV text - Thanks Bruce M.
[*]18/06/2008	Fixed incorrect WSW bearing text translation for Spanish and French - thanks Bruce M. 
[*]18/06/2008	Updated to now use users own registration details from weather.com, visit [http://www.weather.com/services/xmloap.html](http://www.weather.com/services/xmloap.html) to register and obtain the PAR and KEY codes
[/LIST]
The change that you should all pay close attention to is requirement for registration details to run any new scripts from this point on. Sorry for the inconvenience, but it is necessary due to the level of requests which are now being made of the Weather XOAP service. I have detailed the registration steps and reasons in step 4 in the first post.

**[COLOR="Blue"]NOTE: You might want to wait until you receive your registration details before updating the script, otherwise you might be without weather forecasting for a day or so....[/COLOR]**

Cheers,
Mark

[COLOR="Blue"]===============================================================================================[/COLOR]
[COLOR="Blue"]**[SIZE="3"]Step 4: Weather.com XOAP Service Registration[/SIZE]**[/COLOR]

Due to the risk of having the previously registered xoap weather.com account terminated because of high volumes of requests, I have upgraded the script to use a users own registered details. 

The following are the lines in the script, which will require your own registration codes:

```
XOAP_PAR = u"1234567890" #Invalid code, needs replacing
XOAP_KEY = u"ac12ab12ab12ab12" #Invalid code, needs replacing
```

To register and obtain the necessary codes you need to visit [http://www.weather.com/services/xmloap.html]("http://www.weather.com/services/xmloap.html") and fill out the required form. 

After successfully completing the form, you will then receive a couple of emails providing you with the necessary codes to update conkyForecast with, along with the software development kit and terms and conditions.

[COLOR="Blue"]===============================================================================================[/COLOR]

---

### Post by wnelson on 2008-06-18
Thank you for a great addon to conky. Totally awsome.

Thanks
Walt

---

### Post by kaivalagi on 2008-06-19
> **wnelson said:**
> Thank you for a great addon to conky. Totally awsome.

Thanks
Walt

My pleasure :)

---

### Post by DaveKong on 2008-06-19
I haven't gotten my conky set up yet but I got to the xoap subscription part I noticed that in the terms of use it says you must advertise for TWCi and I can see from screen shots and know personally there is no way I would put advertisement links on my desktop. Their website says the data can be used for a desktop application but then it seems strange that they would still require advertisements... Has anyone talked to TWI about using the subscription in the way suggested by this thread? They may not be happy if they find out tons of people are using it for conky and breaking the terms of use agreement. I just tried calling and did not get through to anyone but may try some more. They have automated answering and I am not exactly sure who I should be talking to.

---

### Post by HippyRandall on 2008-06-19
I highly doubt that this is a matter of breaking the EULA since they offer their own desktop gadgets and google widgets. I would be happy to change my "Weather" title on my conky to "Weather from TWCi" if they really wanted to be sticklers about it but how exactly would they know whether or not I changed it? Even if they required a SS of the conky I could easily change it to whatever I wanted after.
Seems like a no point to me. I use their widget/gadget on my website so I don't think they are really going to care one way or the other.
And really, why open a can of worms by calling? Not sure what you think would happen should they find out but I don't think the feds will come banging down your door to confiscate the offending computer.

Just my 2cents and not trying to be rude,
Hippy

---

### Post by kaivalagi on 2008-06-19
> **DaveKong said:**
> I haven't gotten my conky set up yet but I got to the xoap subscription part I noticed that in the terms of use it says you must advertise for TWCi and I can see from screen shots and know personally there is no way I would put advertisement links on my desktop. Their website says the data can be used for a desktop application but then it seems strange that they would still require advertisements... Has anyone talked to TWI about using the subscription in the way suggested by this thread? They may not be happy if they find out tons of people are using it for conky and breaking the terms of use agreement. I just tried calling and did not get through to anyone but may try some more. They have automated answering and I am not exactly sure who I should be talking to.

I originally came up with the idea of using thier XOAP service as that is what's used in the weather applet in the Avant Window Manager...

If I could include their logo I would, however this is not possible as conky output is text only. As HippyRandall has suggested, you could always add some text implying the data is sourced from them, in fact, based on this I shall update the examples I provide in the first post shortly to include some information. [COLOR="Blue"]Examples in conkyForecast.tar.gz now updated :)[/COLOR]

I believe, on the basis that the data retrieved is used solely in a users own conky setup, and that they know it has come from weather.com, that is advertising enough. The script is not being used commercially.

I am sure we are all grateful of the accurate data weather.com provides and know to visit their website for further information on weather around the globe.

Also, the script is still in development and as such is being tested by users with their own registration codes.

Enough said I think.

---

### Post by Bruce M. on 2008-06-19
When I registered I did this:

Proposed Usage: Desktop Application
Description: Conky in Linux

No problem.
Bruce

---

### Post by kaivalagi on 2008-06-19
> **Bruce M. said:**
> When I registered I did this:

Proposed Usage: Desktop Application
Description: Conky in Linux

No problem.
Bruce

I did exactly the same for the initial registration I made

---

### Post by HippyRandall on 2008-06-19
same here but with the added module for a website

methinks someone is trying to throw stones at a bee's nest for no good reason

Just my 2cents take it or leave it,

Hippy

---

### Post by Bruce M. on 2008-06-19
> **HippyRandall said:**
> same here but with the added module for a website

methinks someone is trying to throw stones at a bee's nest for no good reason

Just my 2cents take it or leave it,

Hippy

Never though of that I can pop it into my "local" homepage as well, not on the net just here at home.  :)

Quite happy to use K's registration though

After a while those 2cents add up, be careful where you toss 'em, I'm a collector.  :)

---

### Post by HippyRandall on 2008-06-19
> **Bruce M. said:**
> 
Quite happy to use K's registration though


You did get your own ID and Keys now that the newest script requires you to change the fields though right?

> After a while those 2cents add up, be careful where you toss 'em, I'm a collector.  :):lolflag:wanted to toss something else around but trying tokeep it clean and family friendly here in the wonderful world of conkyForecast.py :lolflag:
Just don't understand people who want to stir up trouble for no apparent reason.

crap...another 2cents gone :lolflag:
Hippy

---

### Post by Bruce M. on 2008-06-19
> **HippyRandall said:**
> You did get your own ID and Keys now that the newest script requires you to change the fields though right?

**Nope!** Got them and used them, *before* that happened.

> **HippyRandall said:**
> :lolflag:wanted to toss something else around but trying tokeep it clean and family friendly here in the wonderful world of conkyForecast.py :lolflag:
Just don't understand people who want to stir up trouble for no apparent reason.

That's OK, I like clean .... besides, I hate angry bees!

> **HippyRandall said:**
> crap...another 2cents gone :lolflag:
Hippy

Yippee! 4cents now! See what I mean; I like ckean!

This is better than a "Swear Box" :lolflag:

CHIMO!
Bruce

---

### Post by Bruce M. on 2008-06-19
Hi Folks...

Anyone out there understand what this error is:
```
bruloo@bruloo:~$ cia
bruloo@bruloo:~$ Conky: desktop window (1000003) is subwindow of root window (4e)
Conky: window type - override
Conky: drawing to created window (1a00001)
Conky: drawing to double buffer
close failed: [Errno 32] Broken pipe
close failed: [Errno 32] Broken pipe

```
It happens when I start my *conkyforecast*:
```
background no
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer left
override_utf8_locale yes
use_xft	yes
font Zekton:size=8
xftfont Zekton:size=8
xftalpha 0.5
update_interval 5.0
uppercase no  # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
default_outline_color black
default_shade_color black
draw_borders no
draw_outline yes  # amplifies text if yes
draw_shades no  # shadecolor black
color0 cyan
color1 lightblue
color2 orange
color3 yellow
color4 wheat
color5 white
color6 white
color7 white
color8 white
color9 black
alignment bottom_left  # or top_left, bottom_left, bottom_right
gap_x 10
gap_y -230 # because of the VOFFSET to get the weather font up to the 2nd day, the negative "gap_y" value brings conky back to the bottom of the screen.
text_buffer_size 1024 # use 1024 for the forecast
no_buffers yes  # Subtract file system buffers from used memory?

TEXT
${alignc}${color4}${font zekton:size=11}El Tiempo - 4 Días$font
${color0}${stippled_hr}$color
${color4}${font zekton:size=9}${execi 3600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --template=/home/bruloo/Conky/scripts/myweather.template}$font$color
${voffset -305}${color3}${font Weather:size=50}${execi 3600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=1}$font$color
${voffset 20}${color3}${font Weather:size=50}${execi 3600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=2}$font$color
${voffset 20}${color3}${font Weather:size=50}${execi 3600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=3}$font$color
${voffset 20}${color3}${font Weather:size=50}${execi 3600 python ~/Conky/scripts/SP_Forecast.py --location=ARBA0009 --datatype=WF --startday=4}$font$color
```
... and *myweather.template* just in case you need it:
```
                  {--datatype=DW --startday=1}:  {--datatype=CC --startday=1}
                  {--datatype=HT --startday=1} / {--datatype=LT --startday=1}       Viento:  {--datatype=WD --startday=1}  a  {--datatype=WS --startday=1}
                  Humedad: {--datatype=HM --startday=1}          Precipitacion: {--datatype=PC --startday=1}
                  Salida del Sol: {--datatype=SR --startday=1}   Ocaso: {--datatype=SS --startday=1}
-----------------------------------------------
                  {--datatype=DW --startday=2}:  {--datatype=CC --startday=2}
                  {--datatype=HT --startday=2} / {--datatype=LT --startday=2}       Viento:  {--datatype=WD --startday=2}  a  {--datatype=WS --startday=2}
                  Humedad: {--datatype=HM --startday=2}          Precipitacion: {--datatype=PC --startday=2}
                  Salida del Sol: {--datatype=SR --startday=2}   Ocaso: {--datatype=SS --startday=2}
-----------------------------------------------
                  {--datatype=DW --startday=3}:  {--datatype=CC --startday=3}
                  {--datatype=HT --startday=3} / {--datatype=LT --startday=3}       Viento:  {--datatype=WD --startday=3}  a  {--datatype=WS --startday=3}
                  Humedad: {--datatype=HM --startday=3}          Precipitacion: {--datatype=PC --startday=3}
                  Salida del Sol: {--datatype=SR --startday=3}   Ocaso: {--datatype=SS --startday=3}
-----------------------------------------------
                  {--datatype=DW --startday=4}:  {--datatype=CC --startday=4}
                  {--datatype=HT --startday=4} / {--datatype=LT --startday=4}       Viento:  {--datatype=WD --startday=4}  a  {--datatype=WS --startday=4}
                  Humedad: {--datatype=HM --startday=4}          Precipitacion: {--datatype=PC --startday=4}
                  Salida del Sol: {--datatype=SR --startday=4}   Ocaso: {--datatype=SS --startday=4}
```
It's probably a missed comma or some such silly thing but for the life of me I can't find it. :confused:

Thanks...
Bruce

---

### Post by kaivalagi on 2008-06-19
> **Bruce M. said:**
> Hi Folks...

Anyone out there understand what this error is:
```
bruloo@bruloo:~$ cia
bruloo@bruloo:~$ Conky: desktop window (1000003) is subwindow of root window (4e)
Conky: window type - override
Conky: drawing to created window (1a00001)
Conky: drawing to double buffer
close failed: [Errno 32] Broken pipe
close failed: [Errno 32] Broken pipe

```
It happens when I start my *conkyforecast*


I have seen some of those errors in the past too, for me they were intermittent. I've seen them most when messing around with lots of text from rss feeds in conky, it may have something with large amounts of text being output to the screen. Your conky setups seem quite high on the amount of text...

It's just a guess but why not try adding the following to your conky config settings and see how you get on:

```
text_buffer_size 512

```

It may well alter conky's internal behaviour with all that text...?

Other than that suggestion I'm stumped!

---

### Post by HippyRandall on 2008-06-19
with the text_buffer_size 1024 that you have set now you are still running out of room. the last sunset in your conky is getting cut off. my suggestion would be to eliminate some spacing or something so you cans see the whole output.

Two more for ya Bruce! (grumbles about losing all these 2c in a row in one day :lolflag:)

Hippy

---

### Post by Bruce M. on 2008-06-19
> **kaivalagi said:**
> I have seen some of those errors in the past too, for me they were intermittent. I've seen them most when messing around with lots of text from rss feeds in conky, it may have something with large amounts of text being output to the screen. Your conky setups seem quite high on the amount of text...

It's just a guess but why not try adding the following to your conky config settings and see how you get on:

```
text_buffer_size 512

```

It may well alter conky's internal behaviour with all that text...?

Other than that suggestion I'm stumped!

I had it at 512 and needed more, been using 1024 for a while now:(
```
text_buffer_size 1024 # use 1024 for the forecast
```
Just pumped that up to 1152 and it worked, and caught the last few characters that were missing (just noticed those) - see the image in the original post, that last line sunset time 5: ??? missing a bit.

I knew it was something simple that I was missing. Too many trees in the forest!

Thanks K
CHIMO!
Bruce

---

### Post by Bruce M. on 2008-06-19
> **HippyRandall said:**
> with the text_buffer_size 1024 that you have set now you are still running out of room. the last sunset in your conky is getting cut off. my suggestion would be to eliminate some spacing or something so you cans see the whole output.

Two more for ya Bruce! (grumbles about losing all these 2c in a row in one day :lolflag:)

Hippy

[CENTER][SIZE="7"][COLOR="Blue"]YES![/COLOR] [COLOR="Red"]6[/COLOR][COLOR="Blue"]cents![/COLOR][/SIZE]
**At this rate I'll be rich in ¿¡!?**

Rich = z Years = k
z(k) = r (1/n) [ COs( ((theta)+ 2(PI)k)/n ) + i sin( ((theta)+ 2(PI)k)/n ) ]

**Really! That long! :(**[/CENTER]

:lolflag: and problem solved too. Or better ... reduced the dotted lines so they are just under the fonts ... and go back to 1024.

[CENTER][[IMG]http://img256.imageshack.us/img256/5526/4dayscr3.th.gif[/IMG]](http://img256.imageshack.us/my.php?image=4dayscr3.gif)[/CENTER]

---

### Post by DaveKong on 2008-06-19
Thanks for all the cents. I didn't expect so much of a reaction and so fast. I never left a phone message but did send a note asking about use of their service for desktop applications. I think you guys are probably right. Good to give some credit as to where the data came from but probably want to avoid making a stink out of it. 
 I registered my account for conky on linux and said it was for education, since it is. I am learning and sharing what I learn with others. Took me a little while but I have a fairly decent looking conky now with weather and system data :) .

---

### Post by dccrens on 2008-06-19
kaivalagi,
Work of art bro!! Upgraded to the new script; everything works great! Thanks! Only one question, is there a way to remove the "F" from the imperial temperatures so that rather having "78*F" you can have just the 78* (78 degrees) and drop the "F"?

---

### Post by Bruce M. on 2008-06-19
> **dccrens said:**
> kaivalagi,
Work of art bro!! Upgraded to the new script; everything works great! Thanks! Only one question, is there a way to remove the "F" from the imperial temperatures so that rather having "78*F" you can have just the 78* (78 degrees) and drop the "F"?

Hi...

Try:
```
--hideunits
```

Yea, I agree; it's a great work of art.

---

### Post by kaivalagi on 2008-06-21
[COLOR="Blue"][SIZE="4"]**IDEA - Feedback Please**[/SIZE][/COLOR]

I regularly use Google's calendar as a bridge between work and home. This works great even if I have to use MS Outlook at work.

For home use I have a Google gadget on my desktop displaying the calendar entries, which is great, but I wouldn't mind having the equivalent in conky!

If I create a python script to retrieve calendar entries would anyone find it useful?

If you would, can you please let me know what functionality you would like it to have. Examples of use could be:
[LIST]
[*]Get todays events
[*]Get the next n days events
[*]Get events based on keyword matching in title and description
[/LIST]

I currently have a working script (not conkyfied yet!) which uses the gdata libraries from Google, and returns the next 24 hours of info...so the proof of concept is already done.

So please, let you know what functionality would best suit you so I can try and get something knocked together which suits everyones needs early on. Before I get something published I really want to know what it has to do, so I don't end up re-writing it over and over.

The use of command arguments as in conkyForecast can be used, so base any suggestions on this where possible.

Cheers/Chimo/Salut/Loloma

---

### Post by Bruce M. on 2008-06-21
@ "K"

Ummmmmm ... what's Google's calendar?

Never mind...

Welcome to Google Calendar

Organize your schedule and share events with friends
Wouldn't it be great to be able to keep track of all the events in your life, coordinate schedules with friends and family, and find new things to do -- all with one online calendar? We thought so, too. Learn More

    * Seeing the big picture
      With Google Calendar, you can see your friends' and family's schedules right next to your own; quickly add events mentioned in Gmail conversations or saved in other calendar applications; and add other interesting events that you find online.

    * Sharing events and calendars
      You decide who can see your calendar and which details they can view. Planning an event? You can create invitations, send reminders and keep track of RSVPs right inside Google Calendar. Organizations can promote events, too.
    * Staying on schedule
      You can set up automatic event reminders, including mobile phone notifications, and instantly bring up anything on your calendar with the built-in search tool.

I use Jpilot for my Palm... but nice idea.  :)

Have a nice day.
Bruce

---

### Post by HippyRandall on 2008-06-21
personally I don't use any calendar of any type but as always, willing to help with testing or any other way I can.

Hippy

---

### Post by Bruce M. on 2008-06-21
> **HippyRandall said:**
> personally I don't use any calendar of any type but as always, willing to help with testing or any other way I can.

Hippy

I didn't think of that because I have no data in a GC to call on.

Hey kaivalagi, I still think it is a good idea and if you want to pursue it why not create a new thread: "Conky python script with Google Calendar" and pop your post from here as the first post in there.

CHIMO!
Bruce

---

### Post by kaivalagi on 2008-06-22
> **Bruce M. said:**
> I didn't think of that because I have no data in a GC to call on.

Hey kaivalagi, I still think it is a good idea and if you want to pursue it why not create a new thread: "Conky python script with Google Calendar" and pop your post from here as the first post in there.

CHIMO!
Bruce

Once I have a working conky python script for Google calendar I'll start a new thread. 

Just wanted to gauge conky user opinion where I know I can get some :)

I'm not sure what options would be useful to anyone out there, I guess I can just still to the bear essentials first for the script and go from there... 

Any ideas for functionality before I start proper?

---

### Post by jjgomera on 2008-06-22
google calendar, what's that? :D

---

### Post by HippyRandall on 2008-06-22
[http://www.google.com/calendar/](http://www.google.com/calendar/)
keep track of appointments meetings, etc

---

### Post by kaivalagi on 2008-06-22
Just posted conkyGoogleCalendar on this thread -> [http://ubuntuforums.org/showthread.php?t=837385](http://ubuntuforums.org/showthread.php?t=837385)

:) Feedback welcome as always

---

### Post by Plasma_NZ on 2008-06-23
This guide was good... have achive almost what im after...

Basically i have 5 virtual desktops... .conkyrc - i want on all - which i have achived....

the other 2 conkys.. conkyrc_time and conkyrc_weather - i only want on of of the 5 desktops... how can i  achive this..?

any ideas.?

---

### Post by Plasma_NZ on 2008-06-23
Solved my problem..

---

### Post by kaivalagi on 2008-06-23
> **Plasma_NZ said:**
> Solved my problem..

Can you tell us how you achieved this? Sounds like a very useful thing to know :)

---

### Post by Bruce M. on 2008-06-23
> **Plasma_NZ said:**
> This guide was good... have achive almost what im after...

Basically i have 5 virtual desktops... .conkyrc - i want on all - which i have achived....

the other 2 conkys.. conkyrc_time and conkyrc_weather - i only want on of of the 5 desktops... how can i  achive this..?

any ideas.?

> **Plasma_NZ said:**
> Solved my problem..

> **kaivalagi said:**
> Can you tell us how you achieved this? Sounds like a very useful thing to know :)

+1 on that. I'd like to know too.

---

### Post by HippyRandall on 2008-06-23
+2 on that...crap...there's 2 more for ya Bruce!  :lolflag:
but seriously if you could tell how you managed to get different conkys displaying on different desktops, that would be great.

Thanks in advance,
Hippy

---

### Post by Bruce M. on 2008-06-23
> **HippyRandall said:**
> +2 on that...crap...there's 2 more for ya Bruce!  :lolflag:
but seriously if you could tell how you managed to get different conkys displaying on different desktops, that would be great.

Thanks in advance,
Hippy

That's [COLOR="Red"]**8c**[/COLOR] now.  :)
HEY! My apartment number.  I like that.  :)

---

### Post by Plasma_NZ on 2008-06-24
to display my conkyrc with net upload and ram usage etc... 
i used 

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

To make my other 2 conkys display only on 1 desktop i used

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
```

to view how it looks [http://nikta.orconhosting.net.nz/Desktop_stills/](http://nikta.orconhosting.net.nz/Desktop_stills/)

---

### Post by kaivalagi on 2008-06-24
> **Plasma_NZ said:**
> to display my conkyrc with net upload and ram usage etc... 
i used 

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
```

To make my other 2 conkys display only on 1 desktop i used

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
```

to view how it looks [http://nikta.orconhosting.net.nz/Desktop_stills/](http://nikta.orconhosting.net.nz/Desktop_stills/)

so own_window_type normal and no sticky option causes a conky instance to only display on the first desktop......I'll have to try it out :)

---

### Post by Plasma_NZ on 2008-06-24
> **kaivalagi said:**
> so own_window_type normal and no sticky option causes a conky instance to only display on the first desktop......I'll have to try it out :)

Yep, u can also still drag it around... hence why i have a "status" screen now for weather, times, disk/cpu/hdd usage/temp - and will soon be adding a "news conky" to that desktop aswell..

---

### Post by HippyRandall on 2008-06-25
more toys...man this conky is never going to be finalized on my desktop. so much stuff to do that I may have to set my background to a solid color just so I can see it all :D

---

### Post by Plasma_NZ on 2008-06-25
ok.. 4 conkys, 3 stay on one desktop, and 1 is on all... 

RSS New's, Weather, Time, and my default conkyrc on the very bottem (displays on all screens)

The application on the right of the screen is gkrellm

[IMG]http://nikta.orconhosting.net.nz/Desktop_stills/Desktop_1_resized.png[/IMG]

---

### Post by Ferk on 2008-07-06
Thank you so much!

I think this is a very nice idea
however.. when I run it I get this error:

```

$ conkyForecast.py --location=UKXX0103 --datatype=CC

fetchData:Unexpected error:  <type 'exceptions.IndexError'>
Unable to interrogate the weather data
Traceback (most recent call last):
  File "/home/ferk/bin/conkyForecast.py", line 1383, in <module>
    weather.outputData()
  File "/home/ferk/bin/conkyForecast.py", line 1356, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/ferk/bin/conkyForecast.py", line 704, in getOutputText
    output = WeatherText.conditions_text[self.current_conditions[0].condition_code] 
IndexError: list index out of range

```

any help?

---

### Post by kaivalagi on 2008-07-06
> **Ferk said:**
> Thank you so much!

I think this is a very nice idea
however.. when I run it I get this error:

```

$ conkyForecast.py --location=UKXX0103 --datatype=CC

fetchData:Unexpected error:  <type 'exceptions.IndexError'>
Unable to interrogate the weather data
Traceback (most recent call last):
  File "/home/ferk/bin/conkyForecast.py", line 1383, in <module>
    weather.outputData()
  File "/home/ferk/bin/conkyForecast.py", line 1356, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/ferk/bin/conkyForecast.py", line 704, in getOutputText
    output = WeatherText.conditions_text[self.current_conditions[0].condition_code] 
IndexError: list index out of range

```

any help?

Do you have an internet connection? Try running the same command but with the additional --refetch option...

If that doesn't work post your conkyrc and I'll try to reproduce the problem

---

### Post by Sam Lars on 2008-07-06
I had the same problem, you have to change the end day, because it can't go past 4 or 5 days.

---

### Post by kaivalagi on 2008-07-06
> **Sam Lars said:**
> I had the same problem, you have to change the end day, because it can't go past 4 or 5 days.

Hi Sam, I think your error would have related to the forecast data (i.e. 5th day not available). However if the error relates to current_conditions, like in the error text Ferk has posted, this shouldn't be the case (famous last words :) ).

e.g.
```
    output = WeatherText.conditions_text[self.current_conditions[0].condition_code] 
IndexError: list index out of range
```

I think either:

[LIST=1]
[*]Nothing is coming back from the web or cached file (i.e. --refetch might fix this)
[*]A new condition code is returned which is unknown to the conditions_text list (will require me to do some debugging maybe and adding something to the list...)
[/LIST]

I wouldn't bet my life on it though ;)

---

### Post by HippyRandall on 2008-07-06
could it maybe be a problem of ferk not inserting his own weather.com ID and keys and that it throwing the error?

---

### Post by kaivalagi on 2008-07-06
> **HippyRandall said:**
> could it maybe be a problem of ferk not inserting his own weather.com ID and keys and that it throwing the error?

Good thought, it hadn't occurred to me...just tested that theory out and yes that would cause the exact same error! Nice one Hippy

Ferk, have you registered for your own details to login? Check the first post if not.

I think this means a better error message is in order :)

---

### Post by kaivalagi on 2008-07-06
[COLOR="Blue"][SIZE="4"]**UPDATE**[/SIZE][/COLOR]

Just modified the script to raise a decent error message when an invalid license key is used to retrieve data :)

Dev history on first post as follows:

[*]06/07/2008	Added check for invalid licence key error in returned xml and now display "*** ERROR: Invalid License Key ***" in output if found...

---

### Post by HippyRandall on 2008-07-06
> **kaivalagi said:**
> Good thought, it hadn't occurred to me...just tested that theory out and yes that would cause the exact same error! Nice one Hippy

Ferk, have you registered for your own details to login? Check the first post if not.

I think this means a better error message is in order :)
always happy to help :D and more eyes on a problem can find solutions easier.

---

### Post by Bruce M. on 2008-07-07
> **HippyRandall said:**
> always happy to help :D and more eyes on a problem can find solutions easier.

Good one Hippy, here take your **[COLOR="Blue"]8c[/COLOR]** back, you deserve them. :KS:KS:KS:KS:KS

---

### Post by kaivalagi on 2008-07-07
> **Bruce M. said:**
> Good one Hippy, here take your **[COLOR="Blue"]8c[/COLOR]** back, you deserve them. :KS:KS:KS:KS:KS

:lolflag::lolflag::lolflag:

Who says open source doesn't pay!

---

### Post by HippyRandall on 2008-07-07
:lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by Bruce M. on 2008-07-07
> **kaivalagi said:**
> :lolflag::lolflag::lolflag:

Who says open source doesn't pay!

> **HippyRandall said:**
> :lolflag::lolflag::lolflag::lolflag::lolflag:

My my, aren't we a happy bunch. {deleted: happy face}
----------------
You have included 9 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.
----------------
It wouldn't allow me to add my own happy face. {insert: sad face}

I know: **cheat...**

```
0 0  0 0  0 0  0 0  0 0
 ¿    ¿    ¿    ¿    ¿
\_/  \_/  \_/  \_/  \_/
```
[CENTER]**[COLOR="Blue"][SIZE="6"]ta da![/SIZE][/COLOR]**[/CENTER]

---

### Post by kaivalagi on 2008-07-07
> **Bruce M. said:**
> My my, aren't we a happy bunch. {deleted: happy face}
----------------
You have included 9 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.
----------------
It wouldn't allow me to add my own happy face. {insert: sad face}

I know: **cheat...**

```
0 0  0 0  0 0  0 0  0 0
 ¿    ¿    ¿    ¿    ¿
\_/  \_/  \_/  \_/  \_/
```
[CENTER]**[COLOR="Blue"][SIZE="6"]ta da![/SIZE][/COLOR]**[/CENTER]

Nice ascii art :lolflag:

I noticed that, restrictions like that should be allowed on a linux forum. Disgraceful...where's the fun?

:guitar:   :lolflag:     :guitar:     :lolflag:   :guitar:

[-X      :oops:

---

### Post by killerwhale65 on 2008-07-24
Hello,

I am just testing this, but i do not have any output on my conky from the script. The only thing i can read from the included conkyrc-test is things like wind, wind direction, humidity ... but no data. What could be wrong?

thanks!

Matt

---

### Post by Technoviking on 2008-08-01
Get the following error with this

```
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyForecast.py", line 1387, in <module>
    weather.outputData()
  File "/home/dbasinge/conky/conkyForecast.py", line 1360, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/dbasinge/conky/conkyForecast.py", line 923, in getOutputText
    output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short[self.day_forecast[day_number].day_of_week]
IndexError: list index out of range
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyForecast.py", line 1387, in <module>
    weather.outputData()
  File "/home/dbasinge/conky/conkyForecast.py", line 1360, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/dbasinge/conky/conkyForecast.py", line 927, in getOutputText
    output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
IndexError: list index out of range
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyForecast.py", line 1387, in <module>
    weather.outputData()
  File "/home/dbasinge/conky/conkyForecast.py", line 1356, in outputData
    output = self.getOutputTextFromTemplate(self.options.template)
  File "/home/dbasinge/conky/conkyForecast.py", line 1119, in getOutputTextFromTemplate
    templatelist[i] = self.getOutputText(datatype,startday,endday,night,shortweekday,imperial,hideunits,spaces)
  File "/home/dbasinge/conky/conkyForecast.py", line 936, in getOutputText
    string = self.day_forecast[day_number].high
IndexError: list index out of range
```


> **yousillygoose said:**
> For a recap here is my .conkyrc, template, and screenshot.  Enjoy.

.conkyrc



template file for current weather



template file for H/L weather



There you go. I hope this helps and am glad to take questions to take some heat off of our nice script writer.  I don't belive i can simplify this more into more templates because they can't do weather fonts correctly.  ENjoys

---

### Post by kaivalagi on 2008-08-01
> **Mike said:**
> Get the following error with this

```
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyForecast.py", line 1387, in <module>
    weather.outputData()
  File "/home/dbasinge/conky/conkyForecast.py", line 1360, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/dbasinge/conky/conkyForecast.py", line 923, in getOutputText
    output = output + self.getSpaces(spaces) + WeatherText.day_of_week_short[self.day_forecast[day_number].day_of_week]
IndexError: list index out of range
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyForecast.py", line 1387, in <module>
    weather.outputData()
  File "/home/dbasinge/conky/conkyForecast.py", line 1360, in outputData
    output = self.getOutputText(self.options.datatype,self.options.startday,self.options.endday,self.options.night,self.options.shortweekday,self.options.imperial,self.options.hideunits,self.options.spaces)
  File "/home/dbasinge/conky/conkyForecast.py", line 927, in getOutputText
    output = output + self.getSpaces(spaces) + WeatherText.conditions_weather_font[self.day_forecast[day_number].condition_code]
IndexError: list index out of range
Traceback (most recent call last):
  File "/home/dbasinge/conky/conkyForecast.py", line 1387, in <module>
    weather.outputData()
  File "/home/dbasinge/conky/conkyForecast.py", line 1356, in outputData
    output = self.getOutputTextFromTemplate(self.options.template)
  File "/home/dbasinge/conky/conkyForecast.py", line 1119, in getOutputTextFromTemplate
    templatelist[i] = self.getOutputText(datatype,startday,endday,night,shortweekday,imperial,hideunits,spaces)
  File "/home/dbasinge/conky/conkyForecast.py", line 936, in getOutputText
    string = self.day_forecast[day_number].high
IndexError: list index out of range
```

This error is normally due to the --startday or --endday option being set greater than 4. The weather.com xoap service only provides a total of 5 days forecast data including the current day, which equates to a day number range of 0 to 4. There is a quick mention in gotcha's point 2 in the first post.

I should really put some handling code in there to stop any output...

If this isn't the cause then it could be that your cached forecast data is messed up. In this case your best either deleting the cache files like this:

```
rm /tmp/conkyForecast* 
```

or running the script using the --refetch option, to ensure the cached files in tmp are renewed.

If non of that works then post your conkyrc and template (if your using one) and we can debug it.

Cheers

---

### Post by kaivalagi on 2008-08-01
[COLOR="Blue"][SIZE="4"]**IMPORTANT**[/SIZE][/COLOR]
If you have any questions you'll need to post them on the newer thread here: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
This thread has been outdated
Cheers

---

### Post by jjgomera on 2008-08-01
> **kaivalagi said:**
> [COLOR="Blue"][SIZE="4"]**IMPORTANT**[/SIZE][/COLOR]
If you have any questions you'll need to post them on the newer thread here: [http://ubuntuforums.org/showthread.php?t=869328](http://ubuntuforums.org/showthread.php?t=869328)
This thread has been outdated
Cheers
but what the problem with that, outdate, archived isnt lock

---

### Post by Bruce M. on 2008-08-01
> **jjgomera said:**
> but what the problem with that, outdate, archived isnt lock

But it was locked at one time, I tried to post three times and nothing.
I do see that you posted in it though.

Hmmmmm, maybe we need a "Moderator" to put a final post in there pointing people to this thread and then lock it.

**EDIT:** OOOPS! I'm here. How embarrassing!

---

### Post by kaivalagi on 2008-08-02
> **Bruce M. said:**
> But it was locked at one time, I tried to post three times and nothing.
I do see that you posted in it though.

Hmmmmm, maybe we need a "Moderator" to put a final post in there pointing people to this thread and then lock it.

**EDIT:** OOOPS! I'm here. How embarrassing!

I've asked Mike to re-archive the thread, otherwise I have 2 threads to keep updated :(

---

### Post by moredhel on 2008-08-11
It's all setup great, but how do I make it say celsius instead of fahrenheit? >_<

---

### Post by kaivalagi on 2008-08-11
> **moredhel said:**
> It's all setup great, but how do I make it say celsius instead of fahrenheit? >_<

Please post on the other thread, thanks...

---

### Post by moredhel on 2008-08-11
Sorry which thread? (I've worked it out now anyway)

---

### Post by kaivalagi on 2008-08-11
> **moredhel said:**
> Sorry which thread? (I've worked it out now anyway)

No worries, this thread was readonly for a time so I created a new one, read about 4 posts back. I don't want to manage 2 threads for the same thing.

Any more questions please post on the new one, thanks

---


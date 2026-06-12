---
title: "Conky Weather Revisited V2"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by lvleph on 2008-01-13
**IMPORTANT: Before using the new script be aware that the options have changed ( 03 Feb 08 ), and your conkyrc will most likely need to be updated.**

The original Conky Weather Revisited was too buggy, because of the way Conky handles bash. Still don't know why it is different, but I decided I would write the script in a language I was more familiar with anyway. So I wrote the V2 in perl. I hope that everyone likes what I have done. I will try my best to meet everyone's needs.

Well, I didn't really like the other conky weather scripts that were out there. They just didn't do what I wanted and were too complicated, so I made my own. I hope everyone likes it. 

**Step 0:** Find your city code. You can go to weather.com and put in your city in the search. It will then ask you to select the city that you meant. Select that, once the page has loaded look at the address bar for a number after the last / (it should include letters too).

**Step 1:** This conky setup uses a weather font, which I have attached.
To install the fonts follow the directions below.

1. Make the following directory as root:
```
# sudo mkdir /usr/share/fonts/truetype/myfonts
```
2. Copy the font(s) into the newly created directory:
```
# sudo cp [fonts] /usr/share/fonts/truetype/myfonts
```
3. Run the following to setup your fonts cache:
```
# fc-cache -f -v
```

**Step 2:** Save the following script in a file named **weather.pl** and place it in **~/scripts** folder.

```
#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update $file if set to 0 don't use $file

$leadspace="  "; #spacing before each high low
$trailspace="   "; #spacing after each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="    "; #spacing between each day
$lines="\n\n\n\n"; #each \n represents one line between the days and temps

$Text::Wrap::columns = 58;
$initial_tab=""; #tab before first line in weather output
$subsequent_tab="\t"; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(\d+\%)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Feels like:  $tmf$degree\n";
					print "Humidity:    $hmt\n"; 
					print "Wind:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "$ctext\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #how many days are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		my $count=0;
		my $day=(split "t", $what)[0]; #how many days are we looking for
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$leadspace$high$degree/$low$degree$trailspace";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]dt$/ {
		&file_op; #save weather to $file
		my $count1 = my $count2=0;
		my $day=(split "dt", $what)[0]; #how many days are we looking for
		my $flag=1; #print days once
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if(/<th>(\b.+\b)<\/th>/ && ++$count1<=$day){ #look for the conditions upto specified day
				$days[$count1-1]=$1; #save day
				&day_space($days);
			}
			elsif($high=~/\d+/ && $low=~/\d+/ && ++$count2<=$day){$ttext.=$leadspace.$high.$degree."/".$low.$degree.$trailspace;}
			elsif($count1>=$day && $count2>=$day){print "$dtext\n$lines$ttext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		&usage; #print usage error
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size >= 1000){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub usage { #if correct options haven't been passed usage error
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-5]dt displays days and then high/low temp in chosen system up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud" || $_ =~ "Fog"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain" || "Drizzle"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	$ctext.=$_.$fspaces;
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Today ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```

The usage of the **weather.pl** script above is as follows (also see: Step 4)
```
weather.pl <citycode> <system> <option>
        <citycode> - weather.com city code
        <system> - c for metric or f for imperial
        <option> - Only one option can be entered at a time
                c displays current conditions
                w displays list of current conditions
                cp displays current conditions symbol
                t displays current temp in chosen system
                [1-5]d displays the days up to specified day
                [1-5]dp displays condition symbol for days up to specified day
                [1-5]t displays high/low temp in chosen system up to specified day
                [1-5]dt displays days and then high/low temp in chosen system up to specified day
                [1-7]w displays the weather in words up number specified
                [1-5]p displays conditions for specified day
                [1-5] displays high/low temp in chosen system for specified day
```
[1-5] means the range of numbers from 1 to 5. So if you want 5 days of conditions for Richmond VA USA in Fahrenheit use 
```
weather.pl USVA0652 f 5dp
```

**Step 3:** Make **weather.pl** executable.
```

sudo chmod a+x ~/scripts/weather.pl

```

The script will make a file containing the html code from weather.com. The default is to create a new file every hour. You can adjust how often the file is updated through the $update variable in the script.

**Step 4:** Use the following code for your **conky** file, changing "**USVA0652**" for your city code or ZIP code if you live in the USA, Replace "f" with "c" if you want metric degrees.

```
# UBUNTU-CONKY.

# Update interval in seconds
update_interval 1.0

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
xftfont Candera:size=6
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
alignment top_right
#alignment bottom_left
#alignment bottom_right

# stuff after 'TEXT' will be formatted on screen

TEXT
${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS 
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl USVA0652 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl USVA0652 f t}
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USVA0652 f cp}$font
${voffset -10}${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST 
${voffset -7}$hr $color
${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5dp}${font}$color
${voffset -55}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5dt}
${execi 3600 perl ~/scripts/weather.pl USVA0652 f 7w}
```

This conkyrc should work without any changes to the current script. If you change things the formatting will have to be changed most likely. There are several different variables in the weather.pl script that are used in formatting. Spaces between each day's temps are controlled with the variables $leadingspace and $trailingspace (lines 17 and 18 ). There is also a variable for the spacing between each condition symbol, $fspaces (line 19). The spaces between each day can be controlled with the $dspaces variable (line 20). The number of lines between the days and temps, using the [1-5]dt option, can be controlled using the $lines variable (line 21), each /n represents one line.

The width for the list of weather for each day can be controlled using the $Text::Wrap::columns variable (line 23). The number represent the number of columns. The tab for each days initial line can be controlled with the $initial_tab variable (line 24), where /t represents a tab. Following line tabs can be controlled with $subsequent_tab variable.

**NOTE 1:** If the degree symbol is not printing correctly, it is most likely due to the font you are using. 

**NOTE 2:** This script is very dependent on the html tagging used by weather.com, so when they change that tagging this script won't work any more. However, I plan on staying on top of things like that. Just post here if you have any issues.

**NOTE 3:** Please, give me feed back and let me know what you think would be a useful addition. I would like this script to be the end all of conky weather scripts. My main philosophy is to keep everything simple. I don't want to have outside dependencies, if I can help it.

**Note 4:**You should have ```
use_xft yes
``` set in your conkyrc.

**Note 5:**The text weather given by the option [1-7]w is only available in the imperial system.

**UPDATE: 21 January 2008** Added the ability to print multi-day forecast with just two script runs; one for conditions and one for high/low. Also, added UTF-8 for the degree symbol.
**UPDATE: 22 January 2008** Added the ability to put spaces between condition symbols.
**UPDATE: 03 February 2008** Added the ability to see weather report for next 5 days, combined the days and temps into one script call (can still use the single calls), added list of current weather, added leading and trailing space for temps, and added wintry mix.
**UPDATE: 12 February 2008** Added Fog as cloudy and Drizzle as Rain.

**Thanks LazarusHC for your additions.**

---

### Post by Bruce M. on 2008-01-13
Hi lvleph

I'm here, got your heads up, will check this out later, now I'm going to watch a movie with my wife.

Thanks
Bruce

---

### Post by Bruce M. on 2008-01-14
Hi lvleph

I have my first weather.pl conky working.
Looks good too, but a little heavy on CPU usage.

I made some "format" changes, weather symbols are smaller and then spaced to fit over the high/lows better:

```

${color cyan}$hr$color
${voffset -3}${alignc}${color orange}${font :size=10}Buenos Aires 5 Day Forcast$font$color

${voffset -5}${font weather:size=30}${alignc}${offset -45}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 1p}${offset 25}${color orange}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 2p}${offset 25}${color cyan}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 3p}${offset 24}${color green}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 4p}${offset 23}${color red}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 5p}${font}$color
${alignc}${offset -15}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 1}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 2}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 3}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 4}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 5}
${color cyan}$hr$color

```

---

### Post by lvleph on 2008-01-14
I am going to add an additional feature that will make less cpu intensive for multiday forecasts. But it may take some time, because school just started back up, and I am not use to my teaching schedule and my class schedule yet.

---

### Post by Bruce M. on 2008-01-14
> **lvleph said:**
> I am going to add an additional feature that will make less cpu intensive for multiday forecasts. But it may take some time, because school just started back up, and I am not use to my teaching schedule and my class schedule yet.

That would be GREAT!
School? January? It's summ... OH! Up North, how soon we forget.  :)

I'm a patient man.
Bruce

```
Are we there yet?
```

---

### Post by cdtech on 2008-01-15
Hey Bruce, where did you get your fonts? I only have the black and white. I like the color you have.
Did you redo those yourself?

Been following this thread, seems to work good so far. I'm using the first script and still play'n around with it myself, doesn't seem to be buggie with my PC.

Never mind Bruce, I just got it (FONTS) lol, you can change the color of the fonts. I was thinking image.....duh!

---

### Post by lvleph on 2008-01-15
For some reason the first script had to be run through another script. This was because conky couldn't handle the functions in the bash script. I could have always taken them out, but it was harder to read, ugly, and harder to make changes. This version should be a bit faster than the old version. When I finish the new update one can use just two scripts for 5 days versus 10 scripts for 5 days. This, I hope will help with slower computers. But the formatting of one's weather section in conky will have to be very specific. Looks like even in conky sometimes you have to sacrifice beauty for performance.

---

### Post by lvleph on 2008-01-15
Anyone want to beta test the new version? There are very specific setup criterion for this version. It requires specific font sizes and positioning. I may be able to mess with that a bit, so that the user can input those, but right now there is no way of adjusting besides trial and error in your .conkyrc Anyway, to test it make a new file weather_test.pl in ~/scripts. Now make it executable. If the output is not positioned correctly inside conky mess with the offset. If the temps don't line up correctly you will have to add or subtract spaces from the print on line 76 and most likely adjust the offset in conky.
```
chmod a+x ~/scripts/weather_test.pl
```
Then copy the following code into that file
[php]#!/usr/bin/perl

use Switch;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

if(-e $file){ #does the file exist?
	$date=`date -u +%s`; #get current date in seconds
	$created=`stat -c %Y $file`; #get creation date of file in seconds
	$age=$date - $created; #determine age of file
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "cp" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1°\n"; exit;}
			}
		}
	}
	case /[1-5]dp/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high°/$low°     ";}
		}
	}
	case /[1-5]p/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high°/$low°";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\t1p displays today's conditions
\t\t2p displays tomorrow's conditions
\t\t3p displays 3rd day's conditions
\t\t4p displays 4th day's conditions
\t\t5p displays 5th day's conditions
\t\tc displays current temp in chosen system
\t\t1 displays today's high/low temp in chosen system
\t\t2 displays tomorrow's high/low temp in chosen system
\t\t3 displays 3rd day's high/low temp in chosen system
\t\t4 displays 4th day's high/low temp in chosen system
\t\t5 displays 5th day's high/low temp in chosen system"
	}
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_";
}

print "\n"; # need endline to make things look nice

close FILE;[/php]

Place the following in your .conkyrc, don't forget to backup the original.
```
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl ~/scripts/weather_test.pl USVA0652 f 5dp}${font}$color
${font Candera:size=6}${offset 18}${execi 3600 perl ~/scripts/weather_test.pl USVA0652 f 5d}
```
Don't forget if you change the fonts you will have to play with the formatting in the script, specifically line 76, by adding or removing spaces.

Oh and I found a couple bugs in the original code.
1. If your connection is down when weather first tries to get the forecast it creates a blank file and tries to read from that file for the next hour until it can update it again, even if you restart conky. I will have to write a portion of the code that checks the size of the file.
2. The user can input 5dps and it will just output the 5d output. This is from the way I check cases. This may take some thinking and so it will take longer than problem 1.

---

### Post by cdtech on 2008-01-15
I tried the test script but got tons of errors. I will check them out when I get a little more time though (work time). The weather.pl works good so far, the only issue I have is the character format for the degree symbol, I've tried everything to no avail. I would really like to have that.

---

### Post by Bruce M. on 2008-01-15
Hi cdtech,

I have to do this.
I know I don't have to, but I really do. [COLOR="Red"]**It's the little devil in me.**[/COLOR] :twisted:
So what follows are the thoughts that went through my head as I read each statement.

> **cdtech said:**
> Hey Bruce, where did you get your fonts? I only have the black and white. I like the color you have.
Did you redo those yourself?

What? I downloaded them from here, like anyone else that's trying this script. Did he miss the icon for downloading in the first post? Black and white?
DUH, use the colour command!

> **cdtech said:**
> Been following this thread, seems to work good so far. I'm using the first script and still play'n around with it myself, doesn't seem to be buggie with my PC.

Yup, same here.  Works just fine.  

> **cdtech said:**
> Never mind Bruce, I just got it (FONTS) lol, you can change the color of the fonts. I was thinking image.....duh!

{ had a really good chuckle here }
------------------------
To continue in the present...
Thanks for the chuckle.  It did me good.

Don't you just love it when something is staring you in the face and you can't see it because our mind tries to complicate things.

NO!  :lolflag:

Bruce

---

### Post by cdtech on 2008-01-15
ROFL!

Too many /$tmp, end if, statements......

[ATTACH]56536[/ATTACH]

A little busy but I'm cleaning it up a bit. Thanks for the color Bruce.

---

### Post by lvleph on 2008-01-15
> **cdtech said:**
> I tried the test script but got tons of errors. I will check them out when I get a little more time though (work time). The weather.pl works good so far, the only issue I have is the character format for the degree symbol, I've tried everything to no avail. I would really like to have that.

Can you run the script from the terminal and post the output? ```
perl ~/scripts/weather_test.pl <code> <system> <option>
```

I have fixed the issue with the file being empty in the test version. I want to get the test version fixed and working so that I can post that.

[php]#!/usr/bin/perl

use Switch;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`;

if(-e $file && $size){ #does the file exist and is not empty?
	if($size != 0){
		$date=`date -u +%s`; #get current date in seconds
		$created=`stat -c %Y $file`; #get creation date of file in seconds
		$age=$date - $created; #determine age of file
	}
	else{
		$age=$update+1;
	}
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "cp" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1°\n"; exit;}
			}
		}
	}
	case /[1-5]dp/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high°/$low°     ";}
		}
	}
	case /[1-5]p/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high°/$low°";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day
\t\t2 displays tomorrow's high/low temp in chosen system"
	}
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_";
}

print "\n"; # need endline to make things look nice

close FILE;[/php]

---

### Post by Bruce M. on 2008-01-15
@lvleph and cdtech

I notice these lines in the code:

```

	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high°/$low°\n";}

```

It's interesting because I see both &deg; and ° in those lines.

$deg; here:

```
(-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
```

and here:

```
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;

```

and the ° symbol here:

```
"$high°/$low°\n";}
```

What would happen if &deg;  was replaced with ° ?

Bruce

---

### Post by lvleph on 2008-01-15
> **Bruce M. said:**
> @lvleph and cdtech

I notice these lines in the code:

```

	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high°/$low°\n";}

```

It's interesting because I see both &deg; and ° in those lines.

$deg; here:

```
(-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
```

and here:

```
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;

```

and the ° symbol here:

```
"$high°/$low°\n";}
```

What would happen if &deg;  was replaced with ° ?

Bruce

The &deg is the html encoding for the degree symbol and so that line is where I grab the temperature. The other line is where I print it. If you replace ° with &deg it would just print &deg.

Anyway, I believe I have fixed that issue. I had to figure out how to use utf-8 character encoding. The below code is the fixed test code. The test code should still work the old way, so if it is having trouble with displaying all days at once, just use it the old way.

[php]#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`;

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol

if(-e $file && $size){ #does the file exist and is not empty?
	if($size != 0){
		$date=`date -u +%s`; #get current date in seconds
		$created=`stat -c %Y $file`; #get creation date of file in seconds
		$age=$date - $created; #determine age of file
	}
	else{
		$age=$update+1;
	}
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "cp" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]dp/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree     ";}
		}
	}
	case /[1-5]p/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day"
	}
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_";
}

print "\n"; # need endline to make things look nice

close FILE;[/php]

---

### Post by cdtech on 2008-01-15
This is the results I got.........

```
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 40, near "/<h3>(b.+b)</h3"
        (Missing operator before h3?)
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 50, near "#do we have current temp? Then"
  (Might be a runaway multi-line ?? string starting on line 49)
        (Missing operator before Then?)
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 40, near "/<h3>(b.+b)</h3"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 54, near "} continue"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 54, near "C_A_S_E_2: }"
Execution of /home/bobkat/.scripts/conky-scripts/weather_test.pl aborted due to compilation errors.
```

I'll paste the update and see....

---

### Post by cdtech on 2008-01-15
That one was from the first weather_test.pl, this is the results from your update above......

```
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 50, near "/<h3>(b.+b)</h3"
        (Missing operator before h3?)
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 60, near "#do we have current temp? Then"
  (Might be a runaway multi-line ?? string starting on line 59)
        (Missing operator before Then?)
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 50, near "/<h3>(b.+b)</h3"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 64, near "} continue"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 64, near "C_A_S_E_2: }"
Execution of /home/bobkat/.scripts/conky-scripts/weather_test.pl aborted due to compilation errors.
```

---

### Post by lvleph on 2008-01-15
I knew I should have paid attention to that. I knew what it was as soon as I saw </h3>

the one below should work perfectly. The funny thing is that the original has the same problem, but didn't give you errors.lol
[php]#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`; #get size of $file

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

if(-e $file && $size){ #does the file exist and is not empty?
	if($size != 0){
		$date=`date -u +%s`; #get current date in seconds
		$created=`stat -c %Y $file`; #get creation date of file in seconds
		$age=$date - $created; #determine age of file
	}
	else{
		$age=$update+1;
	}
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "cp" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]dp/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree     ";}
		}
	}
	case /[1-5]p/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day"
	}
}

print "\n"; # need endline to make things look nice

close FILE;

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_";
}[/php]

---

### Post by Bruce M. on 2008-01-15
> **cdtech said:**
> ROFL!

Too many /$tmp, end if, statements......

Then make it permanent!
Besides, who ever heard of a "temp end if" anyway.
I mean when it's "the end" it's **THE END**!

:lolflag:

> **cdtech said:**
> [ATTACH]56536[/ATTACH]

How do you do that?  Mine always end up as an attachment at the end of the post in a "block"

I was hoping it would show up here so I could add:

[CENTER]**RUN! THE BORG ARE COMING!**[/CENTER]

But it didn't so I can't do that.  :rolleyes:  Love your desktop, I don't have the resources for that.  :cry:

> **cdtech said:**
> A little busy but I'm cleaning it up a bit. Thanks for the color Bruce.

No problem. Sharing is what this is all about. ):P

---

### Post by cdtech on 2008-01-15
Still get the same thing...hm?

```
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 50, near "/<h3>(b.+b)</h3"
        (Missing operator before h3?)
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 60, near "#do we have current temp? Then"
  (Might be a runaway multi-line ?? string starting on line 59)
        (Missing operator before Then?)
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 50, near "/<h3>(b.+b)</h3"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 64, near "} continue"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 64, near "C_A_S_E_2: }"
Execution of /home/bobkat/.scripts/conky-scripts/weather_test.pl aborted due to compilation errors.
```

---

### Post by cdtech on 2008-01-15
Hey Bruce, I just insert it as an attachment, and it does its thing. I really didn't notice that until you brought it up, cool......

---

### Post by lvleph on 2008-01-15
> **cdtech said:**
> Still get the same thing...hm?

```
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 50, near "/<h3>(b.+b)</h3"
        (Missing operator before h3?)
Bareword found where operator expected at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 60, near "#do we have current temp? Then"
  (Might be a runaway multi-line ?? string starting on line 59)
        (Missing operator before Then?)
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 50, near "/<h3>(b.+b)</h3"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 64, near "} continue"
syntax error at /home/bobkat/.scripts/conky-scripts/weather_test.pl line 64, near "C_A_S_E_2: }"
Execution of /home/bobkat/.scripts/conky-scripts/weather_test.pl aborted due to compilation errors.
```

It is really strange, the code I pasted and the code I have are two different codes. We will try this again. Try the below code.

```
#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`; #get size of $file

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

if(-e $file && $size){ #does the file exist and is not empty?
	if($size != 0){
		$date=`date -u +%s`; #get current date in seconds
		$created=`stat -c %Y $file`; #get creation date of file in seconds
		$age=$date - $created; #determine age of file
	}
	else{
		$age=$update+1;
	}
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "cp" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]dp/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree     ";}
		}
	}
	case /[1-5]p/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day"
	}
}

print "\n"; # need endline to make things look nice

close FILE;

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_";
}
```

edit: I looked it over what I pasted, so it should work.

---

### Post by cdtech on 2008-01-15
That one works...

But the degree sign is still the same on my screen. Is there a certain font your using to make it show correct?

[ATTACH]56546[/ATTACH]

---

### Post by lvleph on 2008-01-15
You used the conkyrc code that I posted right? If so you are, you using the same font. The problem seems to be your locale settings. What language settings do you have?

Also, I think I may post that version. What do you think?

---

### Post by Bruce M. on 2008-01-15
> **cdtech said:**
> Hey Bruce, I just insert it as an attachment, and it does its thing. I really didn't notice that until you brought it up, cool......

Cool he says!  [SIZE="5"]Cool![/SIZE] Imangine, he just said: [SIZE="6"]cool[/SIZE] to me.

Sure! It's cool when it works for you!

But that's ok. I get things like **[SIZE="5"]38°/26°[/SIZE]** correct in conky.  :tongue:

Now that's [SIZE="7"]COOL![/SIZE] Well, OK, so that's hot, not cool. :lolflag:
Just for your info:  The TV said todays "Sensacion Termica" (Feels Like) was a cool [SIZE="5"]**46.1°C**[/SIZE] that's [SIZE="5"]**114.98°F**[/SIZE] folks!!

> **cdtech said:**
> That one works...

But the degree sign is still the same on my screen. Is there a certain font your using to make it show correct?

I never changed a thing in the .pl scripts, use it as is.
However in my conky (all of them) I use this for fonts:

```

use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5

```

Don't know if it will make a difference but give it a try.
Here is my entire code I call: **conkyw5** and I start it with:

```
bruloo@The-Team:~$ ./.startconkyw5
```

```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
own_window_colour brown
own_window_transparent yes
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes


#  FOR MY INFO
# last month
# ${font DejaVu Sans Mono :size=8}${execi 60 cal -3 | cut -c00-22}
# this month
# ${execi 60 cal}
# next month
# ${execi 60 cal -3 | cut -c45-64}$font
# this month and next month
# ${font DejaVu Sans Mono :size=8}${execi 60 cal -3 | cut -c23-64}$font

# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 2 blank lines below TEXT to clear panel
# add this line below TEXT to test things, remove when finished.

#${color cyan}Fix me: CPU Temp: ${color white}${acpitemp}C $color
#${color red}Test Cmds Above ${hr 3} $color

TEXT


${color cyan}$hr$color
${voffset -3}${alignc}${color orange}${font :size=10}Buenos Aires 5 Day Forcast$font$color

${voffset -5}${font weather:size=30}${alignc}${offset -45}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 1p}${offset 25}${color orange}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 2p}${offset 25}${color cyan}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 3p}${offset 24}${color green}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 4p}${offset 23}${color red}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 5p}${font}$color
${alignc}${offset -15}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 1}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 2}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 3}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 4}${offset 10}${execi 3600 perl ~/scripts/lvlephw2.pl ARBA0009 c 5}
${color cyan}$hr$color


```

---

### Post by Bruce M. on 2008-01-15
> **lvleph said:**
> The &deg is the html encoding for the degree symbol and so that line is where I grab the temperature. The other line is where I print it. If you replace ° with &deg it would just print &deg.

I knew that, I just forgot that I knew that   :)
$deg; of course equals °

> **lvleph said:**
> Anyway, I believe I have fixed that issue. I had to figure out how to use utf-8 character encoding. The below code is the fixed test code. The test code should still work the old way, so if it is having trouble with displaying all days at once, just use it the old way.

:confused: **Old way?** :confused:
First explain the "new way" and I'll know what I'm doing here  :)
Of course you may have to explain old way too.  Don't know yet.

When I came here to Conky Revisited V2 I started doing things the V2 way.

---

### Post by cdtech on 2008-01-15
LOOK! LOOK! LOOK!...........

[ATTACH]56561[/ATTACH]

Finally.

Thanks Bruce. I'll have to have a look-see at my conky config file to see what's causing that weird font. Whatever you set up in your config worked. Thanks a million..

---

### Post by lvleph on 2008-01-15
Okay, i should have said the old V2 way, that is the day by day way. The new test version allows one to print out all 5 days at once, but one can choose to print them one day at a time if one wishes.

---

### Post by lvleph on 2008-01-15
> **cdtech said:**
> LOOK! LOOK! LOOK!...........

[ATTACH]56561[/ATTACH]

Finally.

Thanks Bruce. I'll have to have a look-see at my conky config file to see what's causing that weird font. Whatever you set up in your config worked. Thanks a million..

You have to say how you got it to work. The post is not of much use to others if you just show the results.

---

### Post by cdtech on 2008-01-15
I'm working on it right now, it's a font thing, give me a few and I'll have the solution.......

**UPDATE ::.**

**Problem:** "A" character embedded with the degree symbol in conky config file.

**Solution:**

Within the original .conkyrc file there is a line :

```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
```

Comment out this line as such :

```
# Force UTF8? note that UTF8 support required XFT
# override_utf8_locale no

or just change to yes to override utf8 scripting within your code

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

```

---

### Post by Bruce M. on 2008-01-15
> **cdtech said:**
> LOOK! LOOK! LOOK!...........

Finally.

Thanks Bruce. I'll have to have a look-see at my conky config file to see what's causing that weird font. Whatever you set up in your config worked. Thanks a million..

You have no idea how good this makes me feel.   :)
You're welcome.
Bruce

---

### Post by Bruce M. on 2008-01-15
> **lvleph said:**
> You have to say how you got it to work. The post is not of much use to others if you just show the results.

My guess is these three line here:

```

use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5

```

---

### Post by cdtech on 2008-01-15
LOL, just answered it a few post back. You didn't have the "override_utf8_locale" listed in your configuration file and thats why it worked for you. I just changed my original conkyrc file to include "yes" on that line and it works fine now.

---

### Post by lvleph on 2008-01-15
I should have thought of that. I even said it was a locale problem. When I get a chance I will update the original post to have the all in one version, and directions on how to use it. I will also include cdtech's solution to the degree problem.

---

### Post by Bruce M. on 2008-01-15
> **cdtech said:**
> I'm working on it right now, it's a font thing, give me a few and I'll have the solution.......

**UPDATE ::.**

**Problem:** "A" character embedded with the degree symbol in conky config file.

**Solution:**

Within the original .conkyrc file there is a line :

```
# Force UTF8? note that UTF8 support required XFT
override_utf8_locale no
```

Comment out this line as such :

```
# Force UTF8? note that UTF8 support required XFT
# override_utf8_locale no

or just change to yes to override utf8 scripting within your code

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

```

You're right, I never had that line and every conky I've tried has worked like a charm.

> **cdtech said:**
> LOL, just answered it a few post back. You didn't have the "override_utf8_locale" listed in your configuration file and thats why it worked for you. I just changed my original conkyrc file to include "yes" on that line and it works fine now.

When I tested it I cut and pasted what was below TEXT to my conky script file.
Glad I did now.

> **lvleph said:**
> I should have thought of that. I even said it was a locale problem. When I get a chance I will update the original post to have the all in one version, and directions on how to use it. I will also include cdtech's solution to the degree problem.

Sounds good.
I'm not using the "beta" version yet.  I'm still using the original V2 script.
Let me know then you make the changes and I'll grab it.

Bruce

---

### Post by Bruce M. on 2008-01-15
I have a few questions, slightly off topic but since it was the answer to a problem here, only ***slightly*** off topic.

Questions:

 1. Just what is UTF8 anyway?

 2. If you are not using it what are you using?

 3. Why am I using it? <-- no smart remarks here please. [-o<

---

### Post by cdtech on 2008-01-15
> **lvleph said:**
> I should have thought of that. I even said it was a locale problem. When I get a chance I will update the original post to have the all in one version, and directions on how to use it. I will also include cdtech's solution to the degree problem.

Thank you lvleph, that was driving me crazy. Glad we got it worked out though.

---

### Post by cdtech on 2008-01-15
> **Bruce M. said:**
> I have a few questions, slightly off topic but since it was the answer to a problem here, only ***slightly*** off topic.

Questions:

 1. Just what is UTF8 anyway?

 2. If you are not using it what are you using?

 3. Why am I using it? <-- no smart remarks here please. [-o<

It's just a set of functions used to convert character arrays to and from byte arrays. (as degree=#176)

---

### Post by lvleph on 2008-01-15
[Check out the wikipedia entry for utf-8.](http://en.wikipedia.org/wiki/Utf8)

---

### Post by Bruce M. on 2008-01-16
> **cdtech said:**
> It's just a set of functions used to convert character arrays to and from byte arrays. (as degree=#176)

> **lvleph said:**
> [Check out the wikipedia entry for utf-8.](http://en.wikipedia.org/wiki/Utf8)

OK, that explains it why it's so easy for me to type " ° ".
I have Spanish language pack installed and a Spanish keyboard.
DUH!  I should have known that.

Thanks guys
Bruce

---

### Post by lvleph on 2008-01-21
Updated to latest version, which includes multi-day forecasts.

I think I may work on a detailed current conditions, next. Anyone have a request? I will try to get to it as soon as I have time. As you can tell I have been a little slow on the updates compared to before, and it will probably remain that way for any in depth updates until the semester is over.

---

### Post by Bruce M. on 2008-01-22
> **lvleph said:**
> Updated to latest version, which includes multi-day forecasts.

I think I may work on a detailed current conditions, next. Anyone have a request? I will try to get to it as soon as I have time. As you can tell I have been a little slow on the updates compared to before, and it will probably remain that way for any in depth updates until the semester is over.

Post a screenshot  :)

The original is a multi-day (5) forecast.  What did you add different?

REQUESTS: (in order of preference)
 1. What exists today is a 5 day forecast with the weather fonts, repeat that again BELOW the existing days 1 - 5 for days 6 - 10 (see attached example)

As you saw in my other conky:
DAY 02: low to high - conditions
DAY 03: low to high - conditions, etc match what you have for the 5 days, only your temps are high/&#314;ow not low/high (who cares, it's obvious)

 2. Sun Rise - Set and Moon Day - Phase (I've been interested in this for years.
 3. Have **all** info in weather.pl **on** by default, but explain how to comment out code to turn it **off** if you don't require/want it.

Umm . that would change to **Buenos Aires 10 Day Forecast** obviously.

---

### Post by lvleph on 2008-01-22
The original; one had to output each days forecast one at a time, this required 10 script calls for 5 days. The new version stream lines this if one chooses, and allows just 2 script calls for 5 days. Basically, instead of ```
${voffset -5}${font weather:size=50}${alignc}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 1p}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 2p}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 3p}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 4p}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5p}${font}$color
${alignc}${offset -15}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 1}${offset 10}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 2}${offset 10}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 3}${offset 10}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 4}${offset 10}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5}
```
We have something much shorter
```
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5dp}${font}$color
${offset 18}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5d}
```

As for having everything on by default... Because of the weather font, the user has to choose what to output for each script call. So the command for sunrise and such would just have a different option and no code would be changed. However, I could make the script do current weather, including sunrise, sunset, wind speed, wind direction, etc. with one call and have it formatted based on some format file that I would provide.

If conky would allow a script to choose font and color, then I could write the script to do everything all at once. Maybe it does, but I have not seen anything that suggests that it does. Let me know if you know different.

---

### Post by Bruce M. on 2008-01-22
For some reason the new version isn't calling up the font correctly.  Even though it is the same command as the old one which still works perfectly.

I also notice that the new script doesn't appear to be collecting and saving a temp weather file.

---

### Post by lvleph on 2008-01-22
> **Bruce M. said:**
> For some reason the new version isn't calling up the font correctly.  Even though it is the same command as the old one which still works perfectly.

I also notice that the new script doesn't appear to be collecting and saving a temp weather file.
Okay, so it seems from your image that the conditions portion is giving some sort of error. Can you run the following in terminal and give me the output.
```
perl ~/scripts/weather.pl <citycode> c 5dp
``` where <citycode> is the city code you use.

Note: You obviously made name changes and whatever, so just keep that in mind when running the script from terminal.

Oh and let's see your conkyrc for that conky output.

---

### Post by Bruce M. on 2008-01-22
> **lvleph said:**
>  ... with one call and have it formatted based on some format file that I would provide.

This is where you will loose a lot of people using your code.

You choose how it looks and what info that is there.

For that reason why not just stay with a 10 day forcast as I mentioned earlier.

It looks great, it is functional and would eliminate **ugly**:

```
DAY 02: 21C to 29C - Mostly Sunny
......
Day 09: 17C to 29C - Mostly Cloudy

```
that I have.

Some people like conky across their screen, some going down the side like mine.

Yours as it exists (the old one) fits in my conky perfectly, width wise. I took it out and added it to the lower left corner because I wanted the 10 day forecast.  Also with yours I call for info every 4 hours (14400) because it is a "pure" hi/low, conditions for the number of days.  My conkymain calls in at 10 minutes (600) because of the "actual" temp.

---

### Post by Bruce M. on 2008-01-22
> **lvleph said:**
> Okay, so it seems from your image that the conditions portion is giving some sort of error. Can you run the following in terminal and give me the output.
```
perl ~/scripts/weather.pl <citycode> c 5dp
``` where <citycode> is the city code you use.

Note: You obviously made name changes and whatever, so just keep that in mind when running the script from terminal.

Oh and let's see your conkyrc for that conky output.

```

bruloo@The-Team:~$ perl ~/scripts/lvl-w.pl ARBA0009 c 5dp
--13:38:37--  http://weather.yahoo.com/forecast/ARBA0009_c.html
           => `-'
Resolving weather.yahoo.com... 69.147.78.254
Connecting to weather.yahoo.com|69.147.78.254|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [        <=>                          ] 32,079        16.88K/s             

13:38:39 (16.84 KB/s) - `-' saved [32079]

cAcci
bruloo@The-Team:~$ 

```

```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes


#  FOR MY INFO
# C A L E N D A R
# last month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c00-22}
# this month
# ${execi 7200 cal}
# next month
# ${execi 7200 cal -3 | cut -c45-64}$font
# this month and next month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c23-64}$font

# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 3 blank lines below TEXT to clear panels
# add this line below TEXT to test things, remove when finished.

#${color cyan}Fix me: CPU Temp: ${color white}${acpitemp}C $color
#${color red}Test Cmds Above ${hr 3} $color

#Intel Motherboard D815EEA - System Temps
#${color orange}System Temps: ${color cyan}(Low = 0°C / High = 127°C)$color
#${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed '/^$/d'}$color

# Commands TESTED:
#${color orange}CPU Temp: ${color cyan}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c12-17 | sed '/^$/d'}${color orange}°C$color
#${color orange}M/B Temp: ${color cyan}${execi 8 sensors | grep -A 1 'M/B Temp:' | cut -c12-17 | sed '/^$/d'} ${color orange}°C$color
#${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | sed '/^$/d'}$color
#${color cyan}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed '/^$/d'}$color

TEXT


${hr}
${voffset -3}${alignc} 5 DAY FORECAST
${voffset -9}${hr}
${voffset -5}${font weather:size=10}${alignc}${execi 3600 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}${font}
${offset 18}${execi 3600 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

```

---

### Post by lvleph on 2008-01-22
> **Bruce M. said:**
> ```

bruloo@The-Team:~$ perl ~/scripts/lvl-w.pl ARBA0009 c 5dp
--13:38:37--  http://weather.yahoo.com/forecast/ARBA0009_c.html
           => `-'
Resolving weather.yahoo.com... 69.147.78.254
Connecting to weather.yahoo.com|69.147.78.254|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [        <=>                          ] 32,079        16.88K/s             

13:38:39 (16.84 KB/s) - `-' saved [32079]

cAcci
bruloo@The-Team:~$ 

```

```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes


#  FOR MY INFO
# C A L E N D A R
# last month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c00-22}
# this month
# ${execi 7200 cal}
# next month
# ${execi 7200 cal -3 | cut -c45-64}$font
# this month and next month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c23-64}$font

# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 3 blank lines below TEXT to clear panels
# add this line below TEXT to test things, remove when finished.

#${color cyan}Fix me: CPU Temp: ${color white}${acpitemp}C $color
#${color red}Test Cmds Above ${hr 3} $color

#Intel Motherboard D815EEA - System Temps
#${color orange}System Temps: ${color cyan}(Low = 0°C / High = 127°C)$color
#${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed '/^$/d'}$color

# Commands TESTED:
#${color orange}CPU Temp: ${color cyan}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c12-17 | sed '/^$/d'}${color orange}°C$color
#${color orange}M/B Temp: ${color cyan}${execi 8 sensors | grep -A 1 'M/B Temp:' | cut -c12-17 | sed '/^$/d'} ${color orange}°C$color
#${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | sed '/^$/d'}$color
#${color cyan}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed '/^$/d'}$color

TEXT


${hr}
${voffset -3}${alignc} 5 DAY FORECAST
${voffset -9}${hr}
${voffset -5}${font weather:size=10}${alignc}${execi 3600 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}${font}
${offset 18}${execi 3600 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

```

You were calling the temp twice. lol
Your text portion should look like this.
```
TEXT


${hr}
${voffset -3}${alignc} 5 DAY FORECAST
${voffset -9}${hr}
${voffset -5}${font weather:size=10}${alignc}${execi 3600 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}${font}
${offset 18}${execi 3600 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

```

The conditions portion has a p at the end. You only had the d which would give you the temps for 5 days.

---

### Post by Bruce M. on 2008-01-22
> **lvleph said:**
> You were calling the temp twice. lol
Your text portion should look like this.

The conditions portion has a p at the end. You only had the d which would give you the temps for 5 days.

That must be the last "p" I went for!

Strange, I cut and pasted the code in there.  Just too quick on mose clicks for my own good.

It's working, now to format it like the old one.  It'll be a LOT easier on my poor old CPU  :)

Thanks

---

### Post by lvleph on 2008-01-22
I actually did it, because you had mentioned that. I didn't even consider how hard it could be on an old CPU.

---

### Post by Bruce M. on 2008-01-22
Hmmm, there is no way to format the spacing of the conditions over the temps.  :(

---

### Post by Bruce M. on 2008-01-22
I'm still playing with this.

Did you realize you've actually created at least **3 levels** of your conky!

 **1. *High Power*** - The old way with 10 execi calls - for power machines - highly configurable.

 **2. *Medium Power*** - with 6 execi calls & medium configuration.

 **3. *Low Power*** - with 2 execi calls, very little configuration. (your latest)

Samples coming soon. I have #2 done and I'm working on a special #1 to show you the Power of it.

Looks Great so far!
Bruce

---

### Post by lvleph on 2008-01-22
Yes, there is. I posted in the directions. Anyway, you will use the offset function and the number of spaces in the variable $spaces (line 13 in weather.pl). Currently, it is set to 5 spaces. If you are using a smaller weather font size you will want less.

I have been trying to think of a more straight forward way, but...

---

### Post by cdtech on 2008-01-22
Hey lvleph,

Nice work, everything seems to be working great so far. I do have one request though, It would be nice to have a default font color for each weather condition, even if its just white. I could change each color within the code to match my weather conditions. I'm working on different weather fonts to give me (One day displayed in the corner, current condition) a colorful look (like a sunny face font), but I have to stick with  whatever color is in conky. So rainy days are red as well as sunny day's, do you know what I mean?

I'm not very good at coding in perl but I've been looking through some books to try and change the font color to no avail.

Thanks lvleph

---

### Post by Bruce M. on 2008-01-22
> **Bruce M. said:**
> 
 **1. *High Power*** - The old way with 10 execi calls - for power machines - highly configurable.

 **2. *Medium Power*** - with 6 execi calls & medium configuration.

Done see image attached.

Here is the one conkytest file that worked them - kept my CPU at 75-100% for the duration as the two of them together made 16 execi calls all at once.

But it was worth it.  :)
```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes

TEXT

${color cyan}$hr$color
${alignc}${color orange}${font :size=10}Buenos Aires 5 Day Forcast$font$color

${voffset -10}${font weather:size=32}${alignc}${offset -77}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 1p}${offset 32}${color orange}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 2p}${offset 32}${color cyan}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 3p}${offset 30}${color gold}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 4p}${offset 32}${color red}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5p}${font}
${color white}${offset 5}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

${color cyan}$hr$color
${color white}ABOVE: MEDIUM POWER Conky with 6 execi calls.
Spacing the weather font (icons).
You could just as easily space the H/L temps I guess.

BELOW: HIGH POWER Conky in a vertical format
This allows space for extra text or maybe commands
${color cyan}$hr$color
${alignc}${color orange}${font :size=10}Buenos Aires 5 Day Forcast$font$color

${voffset -10}${offset 5}${font weather:size=30}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 1p}$font ${voffset -15}${offset 20}${color white}Day 01 Conditions extra text.

${offset 2}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 1}${offset 12}And text here too

${voffset -10}${offset 5}${color orange}${font weather:size=30}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 2p}$font ${voffset -15}${offset 20}${color white}Day 02 Conditions extra text.$color

${offset 2}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 2}${offset 12}And text here too

${voffset -10}${offset 5}${color cyan}${font weather:size=30}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 3p}$font ${voffset -15}${offset 20}${color cyan}Day 03 Conditions extra text.$color

${offset 2}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 2}${offset 12}${color cyan}Text to match colour coding

${voffset -10}${offset 5}${color yellow}${font weather:size=30}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 4p}$font ${voffset -15}${offset 20}${color white}Day 04 Conditions extra text.$color

${offset 2}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 2}${offset 12}And text here too

${voffset -10}${offset 5}${color red}${font weather:size=30}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 5p}$font ${voffset -15}${offset 20}${color yellow}I had fun going this.$color

${offset 2}${execi 14400 perl ~/scripts/lvlephw2.pl ARBA0009 c 2}${offset 12}${color yellow}Pretty good stuff this.

```

> **lvleph said:**
> Yes, there is. I posted in the directions. Anyway, you will use the offset function and the number of spaces in the variable $spaces (line 13 in weather.pl). Currently, it is set to 5 spaces. If you are using a smaller weather font size you will want less.

I have been trying to think of a more straight forward way, but...

OH!  I missed that ](*,) ... more stuff to play with now. Thanks  lvleph :)

---

### Post by lvleph on 2008-01-22
> **cdtech said:**
> Hey lvleph,

Nice work, everything seems to be working great so far. I do have one request though, It would be nice to have a default font color for each weather condition, even if its just white. I could change each color within the code to match my weather conditions. I'm working on different weather fonts to give me (One day displayed in the corner, current condition) a colorful look (like a sunny face font), but I have to stick with  whatever color is in conky. So rainy days are red as well as sunny day's, do you know what I mean?

I'm not very good at coding in perl but I've been looking through some books to try and change the font color to no avail.

Thanks lvlephThere is no way to tell conky the color of any script output using the script, that I know of (I will play around to make sure). The only thing you can do is change them from inside conky. This is part of the reason there is the option to have individual outputs. You could go to conky site and request this addition.

---

### Post by lvleph on 2008-01-22
> **Bruce M. said:**
> I'm still playing with this.

Did you realize you've actually created at least **3 levels** of your conky!

 **1. *High Power*** - The old way with 10 execi calls - for power machines - highly configurable.

 **2. *Medium Power*** - with 6 execi calls & medium configuration.

 **3. *Low Power*** - with 2 execi calls, very little configuration. (your latest)

Samples coming soon. I have #2 done and I'm working on a special #1 to show you the Power of it.

Looks Great so far!
Bruce


I could even make it so that you could grab the forecast between certain days. Not sure the use of it, but...

I am going to work on the 10 day forecast, but that will take an entire recode. So be patient for that one.

---

### Post by Bruce M. on 2008-01-22
> **lvleph said:**
> I could even make it so that you could grab the forecast between certain days. Not sure the use of it, but...

I am going to work on the 10 day forecast, but that will take an entire recode. So be patient for that one.

"God grant me patience, RIGHT NOW!"

Voice off in the distance.

"Right God, I'll wait, please don't hurt me."  [-o<

---

### Post by lvleph on 2008-01-22
> **Bruce M. said:**
> "God grant me patience, RIGHT NOW!"

Voice off in the distance.

"Right God, I'll wait, please don't hurt me."  [-o<
Learn how to perl program. All the code is there, it just needs to be implemented differently. Basically, the code needs to be told how to grab-say days 3-7. The issue is that the page that has weather for 10 days has a different format than the one with 5 days. However, the 10 day format is actually easier to deal with.

---

### Post by aonegodman on 2008-01-22
Hi guys - take a look see please.

Then - Bruce, what do I need to do to correct spacing/placement of degrees text under icons?   Thanks!  :)

---

### Post by Bruce M. on 2008-01-22
> **aonegodman said:**
> Hi guys - take a look see please.

Then - Bruce, what do I need to do to correct spacing/placement of degrees text under icons?   Thanks!  :)

:lolflag: I don't believe this.  We've been playing with the same thing at the same time.

Here is my conkymain
```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes

TEXT

${font :size=10}${alignc}${color cyan}~~== ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color cyan}==~~$color
${alignc}${Color orange}~~== ${color cyan}Canada ${color orange}==~~$color$font
${color orange}Sis${alignr}${color cyan}Winnipeg${color cyan}: ${color white}${tztime Canada/Central %H:%M}$color
${color orange}JBM & CDM & LilSis${alignr}${alignr}${color cyan}London${color cyan}: ${color white}${tztime Canada/Eastern %H:%M}$color

${font :size=10}${alignc}${color cyan}~~== ${alignc}${color white}${exec whoami} @ $nodename ${color cyan}==~~$color$font
${alignc}${color orange}$sysname $kernel ($machine)$color
${font :size=20}${color white}${alignc}${time %H:%M:%S}$color$font
${font :size=12}${color cyan}${alignc}${time %A, %d %b. %Y}$color$font
${color yellow}UpTime:${alignr}$uptime$color
${color cyan}${hr 1}$color
${color orange}System Temps:$color${alignr}(Low = 0°C / High = 127°C)

${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-19| sed '/^$/d'}$color
${color cyan}${hr 1}$color
${color orange}CPU: ${color white}${cpu}% ${color orange}${cpubar cpu0} $color
${color cyan}Freq: ${color white}$freq ${color cyan}MHz${alignr}${color cyan}Running: ${color white}$running_processes ${color cyan}of ${color white}$processes${color cyan}processes $color
${color cyan}Load Avg (${color yellow}Min${color cyan}):$alignr${color yellow}1: ${color white}${loadavg 1}      ${color yellow}5: ${color white}${loadavg 2}     ${color yellow}15: ${color white}${loadavg 3} ${color orange}$color

${color orange}MEM: ${color cyan}RAM: ${color white}$memperc% ${color cyan}(${color white}${mem} ${color cyan}of ${color orange}${memmax}${color cyan}) ${color orange}$membar $color
${color cyan}Memory Buffered:${color white}${alignr 2}${buffers}$color
${color cyan}Memory Cached:${color white}${alignr 2}${cached}$color
${color orange}DISK: ${color cyan}Swap: ${color white}$swapperc% ${color cyan}(${color white}$swap ${color cyan}of ${color orange}${swapmax}${color cyan})${color orange} ${swapbar}$color
${color orange}HD Info ${color cyan}${hr 1}$color
${color cyan}Ubuntu:${alignr}${color white}${fs_free_perc /}% ${color cyan}(${color white}${fs_used /} ${color cyan}of ${color orange}${fs_size /}${color cyan})$color
${color cyan}BruLoo:${alignr}${color white}${fs_free_perc /media/BruLoo}% ${color cyan}(${color white}${fs_used /media/BruLoo} ${color cyan}of ${color orange}${fs_size /media/BruLoo}${color cyan})$color
${color cyan}W2K:${alignr}${color white}${fs_free_perc /media/sda1}% ${color cyan}(${color white}${fs_used /media/sda1} ${color cyan}of ${color orange}${fs_size /media/sda1}${color cyan})$color
${color orange}WEATHER: ${color cyan}${hr 1}$color
${color yellow}${execi 600 ~/scripts/myweather.sh ARBA0009}$color

${voffset -9}${color cyan}${font weather:size=51}${alignc}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}$font$color
${color yellow}${alignc -9}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

${color cyan}${hr 1} $color
${color orange}IP:${alignc}${color white}${addr eth0}$color
${color cyan}Down: ${color white}${downspeed eth0}k/s ${alignr}${color cyan}Up: ${color white}${upspeed eth0}k/s $color
${color cyan}Total: ${color white}${totaldown eth0} ${alignr}${color cyan}Total: ${color white}${totalup eth0} $color
${color cyan}Inbound: ${color white}${tcp_portmon 1 32767 count}          ${color cyan}Outbound: ${color white}${tcp_portmon 32768 61000 count}${alignr}${color cyan}Total: ${color white}${tcp_portmon 1 65535 count} $color
${color orange}Connections: ${color white}${tcp_portmon 32768 61000 count} ${alignr} ${color orange}Service/Port $color${color white}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}$color

```

and for the 5 Day Forecast these are the lines I have in my conkymain above:

```

${voffset -9}${color cyan}${font weather:size=51}${alignc}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}$font$color
${color yellow}${alignc -9}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

```

Now in your weather.pl file, line #13, change the spaces from 5 to 2 as below:

```

$spaces="  "; #spacing between each high low.

```

I'm down to using one conky now  :)

---

### Post by Bruce M. on 2008-01-22
> **lvleph said:**
> Learn how to perl program. All the code is there, it just needs to be implemented differently. Basically, the code needs to be told how to grab-say days 3-7. The issue is that the page that has weather for 10 days has a different format than the one with 5 days. However, the 10 day format is actually easier to deal with.

Perl?  Isn't that something you get from an oyster?
No wait, I remember my grandmother, "knit one, perl two, knit..."  :lolflag:

I don't think I have enough time on planet Earth to learn Perl.  :(

**Seriously:**

If you can have:

```
$spaces="  "; #spacing between each high low.
```

is it possible to add:

```
$fspaces="     "; #spacing between font symbols.
```

and incorporate that into the coding somewhere so the spaces between the font symbols can be adjusted?

Just a thought
Bruce

---

### Post by aonegodman on 2008-01-22
> 

Now in your weather.pl file, line #13, change the spaces from 5 to 2 as below:

```

$spaces="  "; #spacing between each high low.

```

I'm down to using one conky now  :)

My weather.pl is called lvl-w.pl and I don't find a line with that code for spacing, hmmm?

---

### Post by lvleph on 2008-01-22
> **aonegodman said:**
> My weather.pl is called lvl-w.pl and I don't find a line with that code for spacing, hmmm?

Looks like you are not using the newest version? With the version you are using you can play with the offset variable in your conkyrc.

---

### Post by lvleph on 2008-01-22
> **Bruce M. said:**
> Perl?  Isn't that something you get from an oyster?
No wait, I remember my grandmother, "knit one, perl two, knit..."  :lolflag:

I don't think I have enough time on planet Earth to learn Perl.  :(

**Seriously:**

If you can have:

```
$spaces="  "; #spacing between each high low.
```

is it possible to add:

```
$fspaces="     "; #spacing between font symbols.
```

and incorporate that into the coding somewhere so the spaces between the font symbols can be adjusted?

Just a thought
Bruce
Done. Check the original post. $spaces is on line 14 and $fspaces is on line 15.

---

### Post by Bruce M. on 2008-01-22
> **lvleph said:**
> Done. Check the original post. $spaces is on line 14 and $fspaces is on line 15.

Ahhh, beautiful!  Grabbing it now.
Thanks

Bruce

---

### Post by Bruce M. on 2008-01-22
> **aonegodman said:**
> My weather.pl is called lvl-w.pl and I don't find a line with that code for spacing, hmmm?

You're using an old one I think.  Easy way to tell.

Old **.pl** file will have 10 execi calls in your conky file, hard on resources.

New **.pl** file has 2 execi calls in your conky file, easier on resources.

So check your conky file, if you have 5 execi calls for each of the two lines you have the old file.

Bruce

---

### Post by aonegodman on 2008-01-22
> **lvleph said:**
> Done. Check the original post. $spaces is on line 14 and $fspaces is on line 15.

Right you are. I got the last code you posted.

But please note the following - I went back to first post and grabbed the section mentioned and placed it in proper place,  added some spaces - no effect.

So kept looking down through your code and found the following:

```


#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree         ";}


```

I found by adding spaces after degree it moved the high/low text to the right under the weather fonts. My temps have now lined up. Thanks!

---

### Post by lvleph on 2008-01-22
You didn't need the spaces. You are still using the old way. You have the new script but you are still running it 10 times. Any way, the way you are using it all you needed to do was play with the offset (between each execi), which is in the conkyrc file. The way you did it will work, but I wouldn't sugest doing it that way.

---

### Post by Bruce M. on 2008-01-22
Hi aonegodman

Take note of what lvleph just told you.  You are running the *OLD* **.pl** script with 10 execi runs, hard on the CPU.

> **lvleph said:**
> You didn't need the spaces. You are still using the old way. You have the new script but you are still running it 10 times. Any way, the way you are using it all you needed to do was play with the offset (between each execi), which is in the conkyrc file. The way you did it will work, but I wouldn't sugest doing it that way.

Go to the first post here and grab the **new .pl** script, only 2 execi calls, a lot easier on the CPU.   :)

> **aonegodman said:**
> Right you are. I got the last code you posted.

But please note the following - I went back to first post and grabbed the section mentioned and placed it in proper place,  added some spaces - no effect.

So kept looking down through your code and found the following:

```


#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree         ";}


```

I found by adding spaces after degree it moved the high/low text to the right under the weather fonts. My temps have now lined up. Thanks!

But the last code I posted was "I think" my conkytest that had both the old and the new .pl scripts - for test purposes.

Anyway now that lvleph has added **$fspaces** I made my weather font smaller and played with the spacings.

Here are the results:
In the *NEW* **.pl** file I used this spacing
```

$spaces="  "; #spacing between each high low.     <-- 2
$fspaces=" "; #spacing between condition symbols. <-- 1

```

And my conky file:
```

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes

TEXT

${font :size=10}${alignc}${color cyan}~~== ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color cyan}==~~$color
${alignc}${Color orange}~~== ${color cyan}Canada ${color orange}==~~$color$font
${color orange}Sis${alignr}${color cyan}Winnipeg${color cyan}: ${color white}${tztime Canada/Central %H:%M}$color
${color orange}JBM & CDM & LilSis${alignr}${alignr}${color cyan}London${color cyan}: ${color white}${tztime Canada/Eastern %H:%M}$color

${font :size=10}${alignc}${color cyan}~~== ${alignc}${color white}${exec whoami} @ $nodename ${color cyan}==~~$color$font
${alignc}${color orange}$sysname $kernel ($machine)$color
${font :size=20}${color white}${alignc}${time %H:%M:%S}$color$font
${font :size=12}${color cyan}${alignc}${time %A, %d %b. %Y}$color$font
${color yellow}UpTime:${alignr}$uptime$color
${color cyan}${hr 1}$color
${color orange}System Temps:$color${alignr}(Low = 0°C / High = 127°C)

${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-19| sed '/^$/d'}$color
${color cyan}${hr 1}$color
${color orange}CPU: ${color white}${cpu}% ${color orange}${cpubar cpu0} $color
${color cyan}Freq: ${color white}$freq ${color cyan}MHz${alignr}${color cyan}Running: ${color white}$running_processes ${color cyan}of ${color white}$processes${color cyan}processes $color
${color cyan}Load Avg (${color yellow}Min${color cyan}):$alignr${color yellow}1: ${color white}${loadavg 1}      ${color yellow}5: ${color white}${loadavg 2}     ${color yellow}15: ${color white}${loadavg 3} ${color orange}$color

${color orange}MEM: ${color cyan}RAM: ${color white}$memperc% ${color cyan}(${color white}${mem} ${color cyan}of ${color orange}${memmax}${color cyan}) ${color orange}$membar $color
${color cyan}Memory Buffered:${color white}${alignr 2}${buffers}$color
${color cyan}Memory Cached:${color white}${alignr 2}${cached}$color
${color orange}DISK: ${color cyan}Swap: ${color white}$swapperc% ${color cyan}(${color white}$swap ${color cyan}of ${color orange}${swapmax}${color cyan})${color orange} ${swapbar}$color
${color orange}HD Info ${color cyan}${hr 1}$color
${color cyan}Ubuntu:${alignr}${color white}${fs_free_perc /}% ${color cyan}(${color white}${fs_used /} ${color cyan}of ${color orange}${fs_size /}${color cyan})$color
${color cyan}BruLoo:${alignr}${color white}${fs_free_perc /media/BruLoo}% ${color cyan}(${color white}${fs_used /media/BruLoo} ${color cyan}of ${color orange}${fs_size /media/BruLoo}${color cyan})$color
${color cyan}W2K:${alignr}${color white}${fs_free_perc /media/sda1}% ${color cyan}(${color white}${fs_used /media/sda1} ${color cyan}of ${color orange}${fs_size /media/sda1}${color cyan})$color
${color orange}WEATHER: ${color cyan}${hr 1}$color
${color yellow}${execi 600 ~/scripts/myweather.sh ARBA0009}$color

${voffset -9}${color cyan}${font weather:size=30}${alignc -2}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}$font$color
${color yellow}${alignc}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

${color cyan}${hr 1} $color
${color orange}IP:${alignc}${color white}${addr eth0}$color
${color cyan}Down: ${color white}${downspeed eth0}k/s ${alignr}${color cyan}Up: ${color white}${upspeed eth0}k/s $color
${color cyan}Total: ${color white}${totaldown eth0} ${alignr}${color cyan}Total: ${color white}${totalup eth0} $color
${color cyan}Inbound: ${color white}${tcp_portmon 1 32767 count}          ${color cyan}Outbound: ${color white}${tcp_portmon 32768 61000 count}${alignr}${color cyan}Total: ${color white}${tcp_portmon 1 65535 count} $color
${color orange}Connections: ${color white}${tcp_portmon 32768 61000 count} ${alignr} ${color orange}Service/Port $color${color white}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}$color

```

**NOTE:**
 1. My regular conky weather section calls every 10 minutes to keep the "current" days stuff ... well ... current.
 2. My **.pl** weather portion calls every 4 hours since it is only the hi/low temps and conditions for today and the next 4 days, it doesn't need to be updated that often.

Below in the attachment on the "left" is the result before I could space the weather font, on the right, after.

Which do you think is better?  I prefer the right! (The current conky I'm running).

---

### Post by lvleph on 2008-01-22
Bruce, the new script can be ran in the same way the old one was run. He is using the new one, but in the old way.

---

### Post by aonegodman on 2008-01-23
> **lvleph said:**
> Bruce, the new script can be ran in the same way the old one was run. He is using the new one, but in the old way.

Ok guys, all this old and new and exci this and that, I'm afraid I'm a little confused and or lost in the code.

SO - if I understand the posts thus far, the original(first) post is now the new.pl(weather.pl) that LVLeph edited,  and I should grab that and use it for my weather.pl.  Is that correct?

Thanks and please pardon my thick skull.  :)

---

### Post by Bruce M. on 2008-01-23
> **aonegodman said:**
> Ok guys, all this old and new and exci this and that, I'm afraid I'm a little confused and or lost in the code.

Confused is my normal state of being.  :)

> **aonegodman said:**
> SO - if I understand the posts thus far, the original(first) post is now the new.pl(weather.pl) that LVLeph edited,  and I should grab that and use it for my weather.pl.  Is that correct?

In a word: YES! \\:D/

> **aonegodman said:**
> Thanks and please pardon my thick skull.  :)

Bet you mine is thicker, I'm always doing:  ](*,) and it doesn't hurt anymore!


EDIT:  Check your existing **.pl** script for your 5 Day Forecast
if on lines 14 and 15 you have these:

```
$spaces="  "; #spacing between each high low.
$fspaces=" "; #spacing between condition symbols.
```
Then you have the newest script.  :)

---

### Post by aonegodman on 2008-01-23
):P   Has the weather service changed something?

Came back after lunch and found the weather fonts had stretched my conky across desktop - where did all those fonts come from?    please  look >

---

### Post by aonegodman on 2008-01-23
> 

EDIT:  Check your existing **.pl** script for your 5 Day Forecast
if on lines 14 and 15 you have these:

```
$spaces="  "; #spacing between each high low.
$fspaces=" "; #spacing between condition symbols.
```
Then you have the newest script.  :)

Well I had just grabbed those two lines and placed them in my existing.pl at that location. Does that count or do I still need the rest of the first *.pl?   :)

---

### Post by lvleph on 2008-01-23
> **aonegodman said:**
> ):P   Has the weather service changed something?

Came back after lunch and found the weather fonts had stretched my conky across desktop - where did all those fonts come from?    please  look >

That means there is some sort of error. Can you run weather from terminal and tell me what the error says.

---

### Post by aonegodman on 2008-01-23
> **lvleph said:**
> That means there is some sort of error. Can you run it weather from terminal and tell me what the error says.

Hi - this is the error I get when starting my conky now:

```


aonegodman@aonegodman-desktop:~$ Conky: /home/aonegodman/.conkyscripts/conkymain3: 67: no such configuration: '${color'

```

I looked it over and haven't found it yet, guess it's looking at line 67 is that right? If so, I'll have to print it off and count them as I'm unable to do so looking at it on the screen.  Don't make sense to me, it did it on it's own after running all morning just fine.

Also, I tried to execute my weather.pl from folder and got same error.  It reloaded my conky upon execution as though I had executed a 'startconky' in terminal.    :confused:

Thanks...

---

### Post by lvleph on 2008-01-23
You can tell gedit to display the line numbers. (edit>>preferences; check show line numbers)

Try running the following in terminal.
```
perl ~/scripts/weather.pl <citycode> f 5dp 
```
Obviously, <citycode> is what ever city code you use in your conkyrc.

Also, post your conkyrc that is giving the error.

---

### Post by aonegodman on 2008-01-23
> **lvleph said:**
> You can tell gedit to display the line numbers. (edit>>preferences; check show line numbers)

Try running the following in terminal.
```
perl ~/scripts/weather.pl <citycode> f 5dp 
```
Obviously, <citycode> is what ever city code you use in your conkyrc.

Also, post your conkyrc that is giving the error.

```


aonegodman@aonegodman-desktop:~$ perl ~/scripts/weather.pl USTN1032 f 5dp
--22:21:54--  http://weather.yahoo.com/forecast/USTN1032_f.html
           => `-'
Resolving weather.yahoo.com... 69.147.80.111
Connecting to weather.yahoo.com|69.147.80.111|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [ <=>                             ] 2,340         --.--K/s             

22:21:54 (1.52 MB/s) - `-' saved [2340]

```

ok thats the weather.pl - No display on desktop.


```


# conkymain - TEST - Bruce M. 01.21.08
# Edited for personalization by aonegodman @ jcsmith.tn@gmail.com
# 

background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes


#  FOR MY INFO
# C A L E N D A R
# last month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c00-22}
# this month
# ${execi 7200 cal}
# next month
# ${execi 7200 cal -3 | cut -c45-64}$font
# this month and next month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c23-64}$font

# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 3 blank lines below TEXT to clear panels
# add this line below TEXT to test things, remove when finished.

# ${color cyan}Fix me: CPU Temp: ${color white}${acpitemp}C $color
# ${color red}Test Cmds Above ${hr 3} $color

# Motherboard - System Temps
# ${color orange}System Temps: ${color cyan}(Low = 0°C / High = 127°C)$color
# ${color gold}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed # '/^$/d'}$color

# Commands TESTED:
# ${color orange}CPU Temp: ${color cyan}${execi 8 sensors | grep -A 1 'CPU # Temp:' | cut -c12-17 | sed '/^$/d'}${color orange}°C$color
# ${color orange}M/B Temp: ${color cyan}${execi 8 sensors | grep -A 1 'M/B # Temp:' | cut -c12-17 | sed '/^$/d'} ${color orange}°C$color
# ${color gold}${execi 8 sensors | grep -A 1 'CPU Temp:' | sed '/^$/d'}    # $color
# ${color cyan}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed # '/^$/d'}$color
# Following commented out and moved above TEXT by aonegodman
# ${color orange}System Temps:$color${alignr}(Low = 0°C / High = 127°C)
# ${color gold}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-19| sed # '/^$/d'}$color
# ${font :size=10}${alignc}${color cyan}~~== ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color cyan}==~~$color
${color white}${tztime America/New_York %H:%M}$color
TEXT
${font :size=10}${alignc}${Color orange}~~== ${color cyan}DAYTON,TN 37321 ${color orange}==~~$color$font
${font :size=10}${alignc}${color cyan}~~== ${alignc}${color white}${exec whoami} @ $nodename ${color cyan}==~~$color$font
${alignc}${color orange}$sysname $kernel ($machine)$color
${color cyan}${hr 1}$color
${font :size=18}${color white}${alignc}${time %H:%M:%S}$color$font
${font :size=10}${color cyan}${alignc}${time %A, %d %b. %Y}$color$font
${color gold}UpTime:${alignr}$uptime$color
${color cyan}${hr 1}$color
${color gold}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color gold}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}$color

${color gold}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${font :size=8}${color cyan}WEATHER: ${hr 1}$color
${color gold}${execi 60 ~/scripts/weather.sh USTN0132}$color
${color cyan}${hr 1}$color
${alignc}${color orange}${font :size=10}Dayton,TN 5 Day Forcast$font$color

${voffset -10}${font weather:size=32}${alignc}${offset -77}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 1p}${offset 32}${color orange}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 2p}${offset 32}${color cyan}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 3p}${offset 30}${color gold}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 4p}${offset 32}${color red}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5p}${font}
${color white}${offset 5}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5d}


```

there's is my conkymain   :)

Ooops!   Here is Line 67:

```


${color white}${tztime America/New_York %H:%M}$color


```

---

### Post by Bruce M. on 2008-01-23
> **aonegodman said:**
> Well I had just grabbed those two lines and placed them in my existing.pl at that location. Does that count or do I still need the rest of the first *.pl?   :)

No, that  doesn't count, because the matching $fspace code is somewhere else in the script file, that will actually translate into the number of spaces you use on line 15.  :)

Go grab the real **.pl** from the first post!

*Monty Hall:  "Will the real **.PL** file please download to aonegodman's system"*
Clap clap clap clap clap clap clap clap clap!

---

### Post by Bruce M. on 2008-01-23
Also this:
```
${color white}${tztime America/New_York %H:%M}$color
TEXT
```

should be like this:
```
TEXT
${color white}${tztime America/New_York %H:%M}$color

```
if you want to see it.  :)

Or like this to comment it out:
```
#${color white}${tztime America/New_York %H:%M}$color
TEXT
```

---

### Post by aonegodman on 2008-01-24
> **Bruce M. said:**
> Also this:
```
${color white}${tztime America/New_York %H:%M}$color
TEXT
```

should be like this:
```
TEXT
${color white}${tztime America/New_York %H:%M}$color

```
if you want to see it.  :)

Or like this to comment it out:
```
#${color white}${tztime America/New_York %H:%M}$color
TEXT
```

Yeah, but what I was trying here was to eliminate the little one line clock above the large one. I still wanted the large digital clock display(see my screenshots). But I didn't see a call for tztime that would set the large one. Does that make any sense?

I'll try commenting out and see if large clock works. Next, I'll grab the other *.pl and replace my existing. Thanks.

---

### Post by aonegodman on 2008-01-24
**Ok my conky is back and I'm back on track. **

Sounds like a line from some R&R song.  :lol:

Did the edits and tweaked the  "     spaces"  thingy.

Thanks to all.  I've learned so much on this trip, for example:

Learned how to run a perl script from the CLI to check.

How to edit script files & add lines to code in Gedit.

How to install fonts and cache them.

How to take screenshots of my desktop and attach them to posts, and on and on -  :)

---

### Post by lvleph on 2008-01-24
Okay, so everything works now? Because I am not sure why you didn't get an output from terminal when you ran it.

---

### Post by Bruce M. on 2008-01-24
> **aonegodman said:**
> **Ok my conky is back and I'm back on track. **
**Now it's time to hit the sack!**  :guitar:
> **aonegodman said:**
> Sounds like a line from some R&R song.  :lol:
Yea it does doesn't it.
> **aonegodman said:**
> Did the edits and tweaked the  "     spaces"  thingy.

Thanks to all.  I've learned so much on this trip, for example:

Learned how to run a perl script from the CLI to check.

How to edit script files & add lines to code in Gedit.

How to install fonts and cache them.

How to take screenshots of my desktop and attach them to posts, and on and on -  :)

And it looks GREAT too!
I'm like you, learned a lot more than just conky doing all this.  :)
And met some great people along the way as well!

---

### Post by aonegodman on 2008-01-24
> **lvleph said:**
> Okay, so everything works now? Because I am not sure why you didn't get an output from terminal when you ran it.

I'm not sure what happened the first time either, but I ran my weather.pl later and it worked fine.

I think I got it under control now - thanks for all your help and this thread. :)

---

### Post by aonegodman on 2008-01-24
> **Bruce M. said:**
> **Now it's time to hit the sack!**  :guitar:

Yea it does doesn't it.


And it looks GREAT too!
I'm like you, learned a lot more than just conky doing all this.  :)
And met some great people along the way as well!

Thanks again - now I'm thinkin' 'bout trying on AWN dock for desktop. Maybe I'll have another cup of coffee first.    :lol:

---

### Post by Bruce M. on 2008-01-24
**For: lvleph**

A few questions:

 1. *Weather.pl* creates a "/tmp/weather.html" but I don't see where it deletes it, and yet I search for it and can't find it.  What happens to that file or just where the heck is it if it's still here?

 2. You are using this line:
```
`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
```
to grab weather info from. Can the code be modified to grab the same type of info from another site?

I have in mind this site:  [Servicio Meteorológico Nacional]("http://www.smn.gov.ar/"), it's closer to home here, same city to be exact.

I have a feeling if I copy weather.pl to a second file (say: bsas-lvlw.pl) and change the wget line to something like this it might be usable:

```
`wget -O - http://www.smn.gov.ar/"$code"_"$system".html > $bsasfile`;
```
Note the change of $file to $bsasfile (Bs. As. is short for **B**ueno**s** **A**ire**s**, a common thing here.

And the current days stuff can be found [here]("http://www.smn.gov.ar/?mod=dpd&id=25").

Am I wrong in what I'm thinking?
I'm not asking you to do it, I'd be willing to try with some help.
Would it entail much in the way of changing your **.PL** file?
I can see where you use things like the HTML code to look for stuff, so I'm sure I could figure that out.  :)

For example, looking for this:
```
<div align=center><img src='pronosticos/Iconos/
```
will get you the ICON image for the day ( see attached )
or looking for this:
```
width=50 height=44 alt=' .. '></div>
		</td>
```
will get you the text: Despejado
```
<div align=center class="font1"><strong>T:</strong>
```
will get you the current temp.

The FIRST instance of the above searches will get you the results for "OBSERVATORIO CENTRAL BUENOS AIRES" the second will get you "AEROPARQUE J. NEWBERY" (the local airport in the city, not the International Airport) 

Of course, not knowing perl, I could get myself lost in a split second too.  :)

Now at the second site [Ver Datos Estación Automática]("http://www.smn.gov.ar/?mod=dpd&id=25") (linked on the first page) gets some really neat stuff for today:

```

Temperatura              29.1°C (Temp) 
Humedad                  Actual 50% (Humidity)
Punto de Rocío           17.6°C (Dew Point)

Sensación Térmica (Feels Like)
1. Temperatura y Viento:   29.1°C  (Feels Like: Wind factor)
2. Temperatura y Humedad:  30.1 °C  (Feels Like: Humidity factor)

Presión Barométrica 	1014.3 hPa (Barometric Pressure)
Viento                  E(86)  (Wind: East at 86°)
                        a 3.2km/hr (speed)
Luvia                    0.0mm  (Rainfall)
ET-Evapotranspiración   4.29 (No idea yet)
Radiación Solar        789 W/m²  (Sun Radiation factor)
Radiación UV           9.8 index  (UV Radiation factor)

```

So what do you think?  Am I totally out to lunch here?

---

### Post by Cammy on 2008-01-24
Got mine working! 

No more silly desklets now. :D

---

### Post by Bruce M. on 2008-01-24
> **Cammy said:**
> Got mine working! 

No more silly desklets now. :D

ahem cough, cough, and the screenshot?

---

### Post by arriagga on 2008-01-24
hi, i really like your conky, can you post your conkyrc

please !

thanks


> **aonegodman said:**
> **Ok my conky is back and I'm back on track. **

Sounds like a line from some R&R song.  :lol:

Did the edits and tweaked the  "     spaces"  thingy.

Thanks to all.  I've learned so much on this trip, for example:

Learned how to run a perl script from the CLI to check.

How to edit script files & add lines to code in Gedit.

How to install fonts and cache them.

How to take screenshots of my desktop and attach them to posts, and on and on -  :)

---

### Post by Cammy on 2008-01-24
> **Bruce M. said:**
> ahem cough, cough, and the screenshot?

haha!

Here ya go.  Wish I could get the days listed just under the clouds though.

---

### Post by aonegodman on 2008-01-25
> **arriagga said:**
> hi, i really like your conky, can you post your conkyrc

please !

thanks

```


# conkymain - TEST -  by Bruce M. 01.21.08
# Edited for personalization by aonegodman @ jcsmith.tn@gmail.com
background yes
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour brown
own_window_transparent yes
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 1.0
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 25
# Subtract file system buffers from used memory?
no_buffers yes


#  FOR MY INFO
# C A L E N D A R
# last month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c00-22}
# this month
# ${execi 7200 cal}
# next month
# ${execi 7200 cal -3 | cut -c45-64}$font
# this month and next month
# ${font DejaVu Sans Mono :size=8}${execi 7200 cal -3 | cut -c23-64}$font

# For international dates & times ${tztime} see: /usr/share/zoneinfo
# Leave 3 blank lines below TEXT to clear panels
# add this line below TEXT to test things, remove when finished.

# ${color cyan}Fix me: CPU Temp: ${color white}${acpitemp}C $color
# ${color red}Test Cmds Above ${hr 3} $color

# Motherboard - System Temps
# ${color orange}System Temps: ${color cyan}(Low = 0°C / High = 127°C)$color
# ${color gold}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed # '/^$/d'}$color

# Commands TESTED:
# ${color orange}CPU Temp: ${color cyan}${execi 8 sensors | grep -A 1 'CPU # Temp:' | cut -c12-17 | sed '/^$/d'}${color orange}°C$color
# ${color orange}M/B Temp: ${color cyan}${execi 8 sensors | grep -A 1 'M/B # Temp:' | cut -c12-17 | sed '/^$/d'} ${color orange}°C$color
# ${color gold}${execi 8 sensors | grep -A 1 'CPU Temp:' | sed '/^$/d'}    # $color
# ${color cyan}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-18| sed # '/^$/d'}$color
# Following commented out and moved above TEXT by aonegodman
# ${color orange}System Temps:$color${alignr}(Low = 0°C / High = 127°C)
# ${color gold}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-19| sed # '/^$/d'}$color
# ${font :size=10}${alignc}${color cyan}~~== ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color cyan}==~~$color
# ${color white}${tztime America/New_York %H:%M}$color
TEXT
${font :size=10}${alignc}${Color orange}~~== ${color cyan}YOURTOWN ${color orange}==~~$color$font
${font :size=10}${alignc}${color cyan}~~== ${alignc}${color white}${exec whoami} @ $nodename ${color cyan}==~~$color$font
${alignc}${color orange}$sysname $kernel ($machine)$color
${color cyan}${hr 1}$color
${font :size=18}${color white}${alignc}${time %H:%M:%S}$color$font
${font :size=10}${color cyan}${alignc}${time %A, %d %b. %Y}$color$font
${color cyan}${hr 1}$color
${color gold}CPU ${hr 2}$color
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
$cpubar
${cpugraph 000000 ffffff}
NAME             PID       CPU%      MEM%
${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color gold}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
Root:  ${fs_free_perc /}%   ${fs_bar 6 /}$color 
Home:  ${fs_free_perc /home}%   ${fs_bar 6 /home}$color

${color gold}NETWORK (${addr eth0}) ${hr 2}$color
Down: $color${downspeed eth0} k/s ${alignr}Up: ${upspeed eth0} k/s
${downspeedgraph eth0 25,140 000000 ff0000} ${alignr}${upspeedgraph eth0 
25,140 000000 00ff00}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768 
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}
${font :size=8}${color cyan}WEATHER: ${hr 1}$color
${color gold}${execi 60 ~/scripts/weather.sh US*****}$color
${color cyan}${hr 1}$color
${alignc}${color orange}${font :size=8}My 5 Day Forcast$font$color

${voffset -10}${font weather:size=32}${alignc}${offset -77}${execi 14400 perl ~/scripts/lvl-w.pl US****** f 1p}${offset 32}${color orange}${execi 14400 perl ~/scripts/lvl-w.pl US****** f 2p}${offset 32}${color cyan}${execi 14400 perl ~/scripts/lvl-w.pl US****** f 3p}${offset 30}${color gold}${execi 14400 perl ~/scripts/lvl-w.pl US****** f 4p}${offset 32}${color red}${execi 14400 perl ~/scripts/lvl-w.pl US***** f 5p}${font}
${color white}${offset 5}${execi 14400 perl ~/scripts/lvl-w.pl US****** f 5d}



```

There u go. You'll have to edit to your specs and change name in weather font section to your weather.pl file. 

NOTE:  This is an edited file of CONKYTEST file contributed to this thread by Bruce M.   :)

---

### Post by aonegodman on 2008-01-25
> **Cammy said:**
> Got mine working! 

No more silly desklets now. :D

G-R-E-A-T !  where is it?  :)

---

### Post by aonegodman on 2008-01-25
> **Cammy said:**
> haha!

Here ya go.  Wish I could get the days listed just under the clouds though.

Oh there it is !    A black & white fan I see. Bet you watch Turner Classic Movies too.  :lol:

Looks good.  I'm sure there is a way to add day names there, and if I know Bruce M. he's probably working on that right now . . .  :lolflag:

I don't have room on my desktop for another line in my conky. I have it squeezed down as far as I could get it to avoid conflict with the AWN addition.  See attachment.

---

### Post by Bruce M. on 2008-01-25
> **Cammy said:**
> haha!

Here ya go.  Wish I could get the days listed just under the clouds though.

4 days, not 5?

Well, that's easy,
 Tomorrow,
 the day after tomorrow,
 the day after that,
 the next day
 and the last day   :lolflag:

---

### Post by aonegodman on 2008-01-25
> **Bruce M. said:**
> 4 days, not 5?

Well, that's easy,
 Tomorrow,
 the day after tomorrow,
 the day after that,
 the next day
 and the last day   :lolflag:

Oh my! U made my day . . . :lol:  good one, I needed that this morning. Thanks Bruce.  :KS

---

### Post by Cammy on 2008-01-25
> **aonegodman said:**
> I don't have room on my desktop for another line in my conky. I have it squeezed down as far as I could get it to avoid conflict with the AWN addition.  See attachment.
On my laptop, I have two separate conkys.  Maybe you could split yours and put the weather somewhere else on your desktop to make more room?

> **Bruce M. said:**
> 4 days, not 5?

Well, that's easy,
 Tomorrow,
 the day after tomorrow,
 the day after that,
 the next day
 and the last day   :lolflag:

You're a silly goose!
:p:p:p:p

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> Looks good.  I'm sure there is a way to add day names there, and if I know Bruce M. he's probably working on that right now . . .  :lolflag:

Hmm, but don't you remember, you and I are the non-programmers here.
However, saying that, I do have something up my sleeve I'm working on, and if it works, days will be the easy part.   :)

> **aonegodman said:**
> I don't have room on my desktop for another line in my conky. I have it squeezed down as far as I could get it to avoid conflict with the AWN addition.  See attachment.

Actually I see where you could get 5 more lines without loosing a thing, just by looking at your screenshot.

From top to bottom:

 1. Remove the blank line from under TEXT, I'm certain it will still show: ~~== DAYTON, TN 37321 ==~~

 2. Lets see here, you have a 
${color cyan}${hr}${color}  <<-- delete this line
${color orange}CPU: ${hr}${color}
-> MHtz   Load (1,5,15 minute stuff)  Temp <<-- I see temp is not working.
${color white}${cpubar cpu0} $color  <<--- and finally this line

Change those three lines to:

${color orange}CPU: ${color white}${cpu}% ${cpubar cpu0} $color
-> MHtz   Load (1,5,15 minute stuff)  Temp <<-- I see temp is not working.

Next line:

 3. All the way down into your "conky weather" portion
You are displaying: Tomorrow, which is the same info as the 2nd day in the 5 Day Forecast --- delete this

 4. Now you have 
 - a blanky line
 - ${color cyan}${hr}
${alignc}${color orange}Dayton, TN 5 Day Forecast
--- 5 weather symbols ----

Hmmm, line 1 says: DAYTON, TN - do you really need it here? - 5 symbols, 5 days.

So if you get rid of the blank line betweem MOON and the cyan line above 5 days (assuming you dropped the Tomorrow: line too), and delete the Dayton, TN 5 Day Forecast line it will save you a total of 5 lines.  :)

Oh, I LOVE that background image, where did you get it?

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> Oh my! U made my day . . . :lol:  good one, I needed that this morning. Thanks Bruce.  :KS

No proble, I love a good chuckle every now and then, keeps the heart ticking.

> **Cammy said:**
> On my laptop, I have two separate conkys.  Maybe you could split yours and put the weather somewhere else on your desktop to make more room?



You're a silly goose!
:p:p:p:p

Nope, a retired albatross actually!

---

### Post by aonegodman on 2008-01-25
> **Bruce M. said:**
> Hmm, but don't you remember, you and I are the non-programmers here.
However, saying that, I do have something up my sleeve I'm working on, and if it works, days will be the easy part.   :)


I knew it .  :)      Thanks for looking at my conkymain , I hadn't noticed those, will make a few adjustments.

> 
Oh, I LOVE that background image, where did you get it?

I knew someone would ask me that. dang it!  I'm not sure at the moment. I have a few places that I grab a background image now and then. I thought it might be ** deviant art**, but they are down at the moment for some reason. When I find it I'll shoot you a link for sure.  :)

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> I knew it .  :)      Thanks for looking at my conkymain , I hadn't noticed those, will make a few adjustments.

Give you more space for: Tomorrow, the day aft.... :lolflag:

> **aonegodman said:**
> I knew someone would ask me that. dang it!  I'm not sure at the moment. I have a few places that I grab a background image now and then. I thought it might be ** deviant art**, but they are down at the moment for some reason. When I find it I'll shoot you a link for sure.  :)

Why not upload it to the Gallery, see the link at the top of every page here.
Put it up as my favorite background or something or other.  :)
Check your PMs, one coming at you.

---

### Post by aonegodman on 2008-01-25
> **Bruce M. said:**
> Give you more space for: Tomorrow, the day aft.... :lolflag:



Why not upload it to the Gallery, see the link at the top of every page here.
Put it up as my favorite background or something or other.  :)
Check your PMs, one coming at you.

SEE!  I just learned something else I didn't know anything about - the Gallery   Doh!

OK - Go get it there  "Plasma_Lamp"  1944x1296 jpeg    :)

---

### Post by bimmerd00d on 2008-01-25
This might be the best addition to Conky i've seen so far.  VERY cool.

---

### Post by aonegodman on 2008-01-25
):P     Here we go again with the c-o-n-k-y-s-t-r-e-t-c-h deal.

I haven't changed a thing in my conky files. It acts like it something that happens upon update from the weather service.  I don't know, take a look at my desktop please.

Now I kinda like all the detail  in the B&W weather fonts, and I noticed that they are in addition to my 5 day forecast.  So where did they come from?????   :confused:

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> ):P     Here we go again with the c-o-n-k-y-s-t-r-e-t-c-h deal.

So tell me, just when are you going to put up a *HowTo: Elastic Conky*?

{ducking the tomatoes}

> **aonegodman said:**
> I haven't changed a thing in my conky files. It acts like it something that happens upon update from the weather service.  I don't know, take a look at my desktop please.

Now I kinda like all the detail  in the B&W weather fonts, and I noticed that they are in addition to my 5 day forecast.  So where did they come from?????   :confused:

Ahhh, but you did make changes, you trimmed 5 lines (3 from the looks of it).

And somewhere between

${color cyan}${hr}
and
${alignc}5 Day Forecast

you made a booboo I'll bet.

Post a part of your code, 3 lines above ${color cyan}${hr} and the end, so we can see it.

---

### Post by Bruce M. on 2008-01-25
Hey there folks, I have a new partition on my hard drive as of today, so of course conky need adjusting to reflect my new HOME partition.

Here is is.  :)

[CENTER]
[[IMG]http://img111.imageshack.us/img111/3706/conkyvz6.th.png[/IMG]](http://img111.imageshack.us/my.php?image=conkyvz6.png)
[/CENTER]

Now that feels some good.  :)

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> SEE!  I just learned something else I didn't know anything about - the Gallery   Doh!

OK - Go get it there  "Plasma_Lamp"  1944x1296 jpeg    :)

Got it, just beautiful.  Thank you

No day is a complete loss if we learn something, no matter what it is.
Quote by: I haven't got a clue Smith.

---

### Post by aonegodman on 2008-01-25
> **Bruce M. said:**
> Hey there folks, I have a new partition on my hard drive as of today, so of course conky need adjusting to reflect my new HOME partition.

Here is is.  :)

[CENTER]
[[IMG]http://img111.imageshack.us/img111/3706/conkyvz6.th.png[/IMG]](http://img111.imageshack.us/my.php?image=conkyvz6.png)
[/CENTER]

Now that feels some good.  :)

Looks good, but could all the [COLOR="DeepSkyBlue"]blue clouds[/COLOR] bespeak the kinda day you've been having or what?  :lol:

---

### Post by aonegodman on 2008-01-25
> **Bruce M. said:**
> So tell me, just when are you going to put up a *HowTo: Elastic Conky*?

{ducking the tomatoes}



Ahhh, but you did make changes, you trimmed 5 lines (3 from the looks of it).

And somewhere between

${color cyan}${hr}
and
${alignc}5 Day Forecast

you made a booboo I'll bet.

Post a part of your code, 3 lines above ${color cyan}${hr} and the end, so we can see it.

Probably!   I'll look it over again. But here's the section I edited:

```


MOON: Icon: </xsl:text><xsl:value-of select="moon/icon"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="moon/t"/>

	</xsl:template>

	<xsl:template match="dayf/day[@d='1']">
<xsl:text>
</xsl:text>
	</xsl:template>
</xsl:stylesheet>

```

That's from weather.xslt file, I removed the section calling for [COLOR="Blue"]Tomorrows[/COLOR] weather.

```

${color cyan}${hr 1}$color
${alignc}${color orange}${font :size=8}5 Day Forcast$font$color

${voffset -10}${font weather:size=32}${alignc}${offset -77}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 1p}${offset 32}${color orange}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 2p}${offset 32}${color cyan}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 3p}${offset 30}${color gold}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 4p}${offset 32}${color red}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5p}${font}
${color white}${offset 5}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5d}

```

In conkymain all I think I did was delete "Dayton,TN" out of 5 Day Forecast. Hmmm. What else?
I know I took the "time up" line out up under big clock also. But I think that's it.

---

### Post by aonegodman on 2008-01-25
NEXT - while we're lookin', I really do like the detail in those b&w weather icons.

How are they called(code)?  Are they part of the weather font package that we d/l'd at the beginning?  I just don't see where they are coming from.   :confused:

---

### Post by Bruce M. on 2008-01-25
1. weather.sxlt, show me from **3 lines above MOON to the end**.

 2. Did you touch your weather.pl (lvl-w.pl) file at all?

Everything I see here looks fine, compared it to mine and only changes I see are for city and f.

:confused:

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> NEXT - while we're lookin', I really do like the detail in those b&w weather icons.

How are they called(code)?  Are they part of the weather font package that we d/l'd at the beginning?  I just don't see where they are coming from.   :confused:

Thoss white things are the "weather font" you use in Day 1 of your forecast, notice only 4 coloured fonts below.  Your Day 1 font was in white, and depending on the "conditions" lvl-w.pl will select one of them to be displayed.

Your error exists between the line:
5 Day Forecast
and the call for Day 2 of the 5 Day'er

Post the code again please.

---

### Post by aonegodman on 2008-01-25
> **Bruce M. said:**
> Thoss white things are the "weather font" you use in Day 1 of your forecast, notice only 4 coloured fonts below.  Your Day 1 font was in white, and depending on the "conditions" lvl-w.pl will select one of them to be displayed.

Your error exists between the line:
5 Day Forecast
and the call for Day 2 of the 5 Day'er

Post the code again please.

```


${font :size=8}${color cyan}WEATHER: ${hr 1}$color
${color gold}${execi 60 ~/scripts/weather.sh USTN0132}$color
${color cyan}${hr 1}$color
${alignc}${color orange}${font :size=10}Dayton,TN 5 Day Forcast$font$color

${voffset -10}${font weather:size=32}${alignc}${offset -77}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 1p}${offset 32}${color orange}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 2p}${offset 32}${color cyan}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 3p}${offset 30}${color gold}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 4p}${offset 32}${color red}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5p}${font}
${color white}${offset 5}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5d}



```

```


<xsl:text>
MOON: Icon: </xsl:text><xsl:value-of select="moon/icon"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="moon/t"/>

	</xsl:template>

	<xsl:template match="dayf/day[@d='1']">
<xsl:text>
Tomorrow: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
<xsl:text>
</xsl:text>
	</xsl:template>
</xsl:stylesheet>


```


```


print "\n"; # need endline to make things look nice

close FILE;

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_$fspaces";
}


```

There are the bottoms of the following three files - conkymain, weather.xslt & lvl-w.pl. :)

---

### Post by Bruce M. on 2008-01-25
> **aonegodman said:**
> Looks good, but could all the [COLOR="DeepSkyBlue"]blue clouds[/COLOR] bespeak the kinda day you've been having or what?  :lol:

No, with the new **.PL** file that only does two execi calls it's easier on my slow computer, but I can only pick one colour for the weather font and one for the hi/lows.

Small price to pay for a slow computer.

You on the other hand are using a mix of the old and the new, (my idea) the weather font for **each day** makes an $execi call to get info, because of that you can apply different colours , font sizes, and spacing very easily in "conky code" not perl.

Then you use just one $execi call to get the temps for all 5 days at once.
Check it out somewhere in here (Conky Weather Revisited V2) and you'll see I also use the pure "old" way to created a weather conky that is vertical in nature.

I called them: **Power, Medium, Low**, I think, you're using Medium, I'm using Low.  :)

EDIT:  Check [51]("http://ubuntuforums.org/showpost.php?p=4185428&postcount=51") and [54]("http://ubuntuforums.org/showpost.php?p=4185992&postcount=54").  54 has an image attached.

---

### Post by Bruce M. on 2008-01-25
gimme a sec, I need to plug this into my conky and test it.

EDIT:  Your code is perfect!

kill conky and restart

---

### Post by aonegodman on 2008-01-25
For good measure here's my [COLOR="Blue"]weather.sh[/COLOR] script

```


#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# Modified by Vredfreak
# The orignal script and xslt can be downloaded from http://pondol.com/weather.tar.gz

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use http://xoap.weather.com/search/search?where=[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=USTN0132

# s=standard units, m=metric units
UNITS=s

# where this script and the XSLT lives#
RUNDIR=~/scripts
# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at http://curl.haxx.se/
CURLCMD=/usr/bin/curl

# get it at http://xmlsoft.org/XSLT/
XSLTCMD=/usr/bin/xsltproc
# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?dayf=10&unit=$UNITS&cc=*"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/weather.xslt

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"


```


Is the "dayf=10"  the font size or is it asking for a 10 day foercast?    ;)

---

### Post by aonegodman on 2008-01-25
> **Bruce M. said:**
> 

I called them: **Power, Medium, Low**, I think, you're using Medium, I'm using Low.  :)

EDIT:  Check [51]("http://ubuntuforums.org/showpost.php?p=4185428&postcount=51") and [54]("http://ubuntuforums.org/showpost.php?p=4185992&postcount=54").  54 has an image attached.

Correct, I'm using medium.

---

### Post by lvleph on 2008-01-25
I don't mean to be a dick but can we keep the discussion on my weather script and not any others. Someone may become confused.

---

### Post by aonegodman on 2008-01-25
I also went back to post #60 where you gave the example of [COLOR="Blue"]LOW[/COLOR]

I have tried plugging that in and messed around with *spaces* things and even changed font sizes.

I'm down to all cyan blue weather fonts with detailed fonts, still stretched half across my desktop.  CRAZY!    :(

Well, gonna give it up for tonight. Get back on it tomorrow.  Thanks.

---

### Post by lvleph on 2008-01-25
> **aonegodman said:**
> I also went back to post #60 where you gave the example of [COLOR="Blue"]LOW[/COLOR]

I have tried plugging that in and messed around with *spaces* things and even changed font sizes.

I'm down to all cyan blue weather fonts with detailed fonts, still stretched half across my desktop.  CRAZY!    :(

Well, gonna give it up for tonight. Get back on it tomorrow.  Thanks.

When I finally get some time I will look into what is going on with your weather. I have barely had time to think as of late.

---

### Post by aonegodman on 2008-01-25
> **lvleph said:**
> When I finally get some time I will look into what is going on with your weather. I have barely had time to think as of late.

Just a quick follow up - weird stuff going on here. My system crashed a few minutes ago and I've spent the last 30 min. getting Ubuntu to come back up.

Don't know really what happened. I went to minimize Firefox and boom - rebooted.

When I get an "unscheduled" reboot like that my CMOS/BIOS looses vision of my Ext. USB HD

where my Ubuntu is ofcourse. I have to use the LiveCD to boot back up and load drivers(I guess) to get BIOS to recognize it again.  Then I can restart and choose my EXT HD as a bootable dev again.

Excuse me for detailing this here, but I said all this to let you know that when I finally got my desktop back, there was conky(not my last config mind you).

No menus at all. Had to figure out how to get taskbar back up and installed Gnome Menu to get to desktop functions going again.

Right now I am unable to change the screen resolution on my desktop and it's got everything so small(high RES) I can't hardley read what I'm typing here.

Anyway, that's where I am right now. 

STOP LAUGHING BRUCE!!!     :lolflag:

Later all -  :)

---

### Post by Cammy on 2008-01-26
> **Bruce M. said:**
> 4 days, not 5?

Sorry, I forgot to answer this.

I have 4 days because I have a narrow conky.  If I do 5 days, the temp readings look like this:

41/2843/2748/3146/32/47/29 and it looks quite cluttered.  If I do 4 days, I can have a space between:

41/28 43/27 48/31 46/32 and it's easier to read.

So I just need to figure out how to get: Sat  Sun  Mon  Tue  ;)

---

### Post by lvleph on 2008-01-26
> **aonegodman said:**
> Just a quick follow up - weird stuff going on here. My system crashed a few minutes ago and I've spent the last 30 min. getting Ubuntu to come back up.

Don't know really what happened. I went to minimize Firefox and boom - rebooted.

When I get an "unscheduled" reboot like that my CMOS/BIOS looses vision of my Ext. USB HD

where my Ubuntu is ofcourse. I have to use the LiveCD to boot back up and load drivers(I guess) to get BIOS to recognize it again.  Then I can restart and choose my EXT HD as a bootable dev again.

Excuse me for detailing this here, but I said all this to let you know that when I finally got my desktop back, there was conky(not my last config mind you).

No menus at all. Had to figure out how to get taskbar back up and installed Gnome Menu to get to desktop functions going again.

Right now I am unable to change the screen resolution on my desktop and it's got everything so small(high RES) I can't hardley read what I'm typing here.

Anyway, that's where I am right now. 

STOP LAUGHING BRUCE!!!     :lolflag:

Later all -  :)

Did you start a thread discussing this? If so link to it so I can try to help from the appropriate thread. As far as conky weather being stretched, if you put spaces between the symbols these spaces might be pretty large if you are using a large font. Try setting the $fspaces=""; and see what happens. If that is not it, I will have to actually look over your conkyrc and the code you are using. But, I just don't have the time right now (grading, my own classes, and organizations).

---

### Post by aonegodman on 2008-01-26
> **lvleph said:**
> Did you start a thread discussing this? If so link to it so I can try to help from the appropriate thread. As far as conky weather being stretched, if you put spaces between the symbols these spaces might be pretty large if you are using a large font. Try setting the $fspaces=""; and see what happens. If that is not it, I will have to actually look over your conkyrc and the code you are using. But, I just don't have the time right now (grading, my own classes, and organizations).

Thank you lvleph for your  response, and yes I have sought help on other thread for desktop problems.

Now I have my desktop back under control( I thinks), I got back to conkyizing.

I have learned much from just going back and forth over the scripts and making minor adjustments.

For one thing, editing should be done in small bites as the script is sensitive for sure.

I switched from "medium" to "low" graphics and execi calls for my 5 day weather calls.

I found [COLOR="Red"]five points[/COLOR] of editing that effects the [COLOR="Cyan"]weather fonts[/COLOR] and [COLOR="Orange"]hi/low[/COLOR] temp settings in this area.

First - these two in the weather.pl or my lvl-w.pl

```

$spaces="      "; #spacing between each high low.
$fspaces=" "; #spacing between condition symbols.

```

and then the following three highlited spots in my conkymain -

```

${voffset[COLOR="Blue"] -8[/COLOR]}${color cyan}${font weather:size=[COLOR="Blue"]37[/COLOR]}${alignc}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5dp}$font$color
${color gold}${alignc [COLOR="Blue"]-1[/COLOR]}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5d}

```

Hope this helps out.    :)

---

### Post by tombug on 2008-01-26
hm i did step by step 3 times and i still get

```
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'

```

yes i have weather in /user/share/fonts/truetype/myfonts

---

### Post by Cammy on 2008-01-26
That should be "**/usr/**share/fonts/truetype/myfonts"

You have an "e" in /usr/

If that's just a post typo, sorry, but maybe you copied it to /user/... and the fonts didn't end up in the right place.

---

### Post by Bruce M. on 2008-01-26
> **aonegodman said:**
> Just a quick follow up - weird stuff going on here. My system crashed a few minutes ago and I've spent the last 30 min. getting Ubuntu to come back up.

{chuckling quietly here, oh, if only he knew!}

> **aonegodman said:**
> Don't know really what happened. I went to minimize Firefox and boom - rebooted.

When I get an "unscheduled" reboot like that my CMOS/BIOS looses vision of my Ext. USB HD

where my Ubuntu is ofcourse. I have to use the LiveCD to boot back up and load drivers(I guess) to get BIOS to recognize it again.  Then I can restart and choose my EXT HD as a bootable dev again.

Excuse me for detailing this here, but I said all this to let you know that when I finally got my desktop back, there was conky(not my last config mind you).

No menus at all. Had to figure out how to get taskbar back up and installed Gnome Menu to get to desktop functions going again.

Right now I am unable to change the screen resolution on my desktop and it's got everything so small(high RES) I can't hardley read what I'm typing here.

Anyway, that's where I am right now.

Yup, I see that, me too

> **aonegodman said:**
> STOP LAUGHING BRUCE!!!     :lolflag:

Later all -  :)

ME!  Laugh at you!  Would I do that after doing [this]("http://ubuntuforums.org/showthread.php?p=4210911#post4210911")?

I don't think so!  :lolflag: <-- you - me--> :lolflag: If we can't laugh at ourselves who can we laugh at?

---

### Post by Bruce M. on 2008-01-26
> **aonegodman said:**
> For good measure here's my [COLOR="Blue"]weather.sh[/COLOR] script

Is the "dayf=10"  the font size or is it asking for a 10 day foercast?    ;)


That's not in the **.pl** stuff, thats for the **.sh** and **.sxlt** part of weather.
It's for the 10 Day Forcast as shown in my older conky before taking it out and putting lvleph's 5 Day Forecast in it's place

Unfortunately, until I do a restore, I can't show you.  :cry:

EDIT:  Yes I can, found it in another post:
the **.xslt** file:
```

<!-- 

 This XSLT is used to translate an XML response from the weather.com
 XML API. 

 You can format this file to your liking. Two things you may feel 
 like doing:

	1) Modify the layout of the fields or static text already defined
	2) Add other fields from the XML response file that aren't referenced in this
	   XSLT. You can grab a full list by just doing a: 
wget "http://xoap.weather.com/weather/local/USTN0132?cc=*&unit=$s"
           (change $LOCID and $UNITS to suit your needs)
-->

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" > 
	<xsl:output method="text" disable-output-escaping="yes"/>
	<xsl:template match="weather">
			<xsl:apply-templates select="loc"/>
			<xsl:apply-templates select="cc"/>
			<xsl:apply-templates select="dayf/day[@d='1']"/>
			<xsl:apply-templates select="dayf/day[@d='2']"/>
			<xsl:apply-templates select="dayf/day[@d='3']"/>
			<xsl:apply-templates select="dayf/day[@d='4']"/>
			<xsl:apply-templates select="dayf/day[@d='5']"/>
			<xsl:apply-templates select="dayf/day[@d='6']"/>
			<xsl:apply-templates select="dayf/day[@d='7']"/>
			<xsl:apply-templates select="dayf/day[@d='8']"/>
	</xsl:template>
	
			<xsl:template match="loc">

<xsl:text>Live from:  </xsl:text><xsl:value-of select="dnam"/>
<xsl:text>
Lat: </xsl:text><xsl:value-of select="lat"/>
<xsl:text>                  Long: </xsl:text><xsl:value-of select="lon"/>
<xsl:text>
SUN:  Rise: </xsl:text><xsl:value-of select="sunr"/>
<xsl:text>     Set: </xsl:text><xsl:value-of select="suns"/>

			</xsl:template>

			<xsl:template match="cc">
<xsl:text>

Temp: </xsl:text><xsl:value-of select="tmp"/><xsl:value-of select="/weather/head/ut"/>

<xsl:text>              Feels Like: </xsl:text><xsl:value-of select="flik"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text>

Conditions: </xsl:text><xsl:value-of select="t"/>
<xsl:text>
Visibility: </xsl:text><xsl:value-of select="vis"/><xsl:text> KM</xsl:text>
<xsl:text>     Humidity: </xsl:text><xsl:value-of select="hmid"/><xsl:text>%</xsl:text>
<xsl:text>
Wind: </xsl:text>
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>0</xsl:text></xsl:when>
	<xsl:otherwise><xsl:value-of select="wind/s"/></xsl:otherwise>
</xsl:choose>
<xsl:value-of select="/weather/head/us"/> 
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>(0 km/h)</xsl:text></xsl:when>
	<xsl:otherwise><xsl:text> (</xsl:text><xsl:value-of select="round(wind/s * 0.6214)"/><xsl:text> mph)</xsl:text></xsl:otherwise>
</xsl:choose>
<xsl:text> (</xsl:text><xsl:value-of select="wind/t"/>
<xsl:text>)</xsl:text>
<xsl:text>
Gusting to: </xsl:text><xsl:value-of select="wind/gust"/>
<xsl:text> km/h</xsl:text>
<xsl:text>
Barometer: </xsl:text><xsl:value-of select="bar/r"/>
<xsl:text> mb ~ </xsl:text><xsl:value-of select="bar/d"/>

<xsl:text>
UV: </xsl:text><xsl:value-of select="uv/i"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="uv/t"/>
<xsl:text>        Dew Point: </xsl:text><xsl:value-of select="dewp"/><xsl:text> °C</xsl:text>

<xsl:text>

MOON: Day: </xsl:text><xsl:value-of select="moon/icon"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="moon/t"/>

	</xsl:template>

	<xsl:template match="dayf/day[@d='1']">
<xsl:text>

DAY 02: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

	<xsl:template match="dayf/day[@d='2']">
<xsl:text>
DAY 03: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

	<xsl:template match="dayf/day[@d='3']">
<xsl:text>
DAY 04: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

	<xsl:template match="dayf/day[@d='4']">
<xsl:text>
DAY 05: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

	<xsl:template match="dayf/day[@d='5']">
<xsl:text>
DAY 06: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

	<xsl:template match="dayf/day[@d='6']">
<xsl:text>
DAY 07: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

	<xsl:template match="dayf/day[@d='7']">
<xsl:text>
DAY 08: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

	<xsl:template match="dayf/day[@d='8']">
<xsl:text>
DAY 09: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<!-- <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/> -->
	</xsl:template>

</xsl:stylesheet>

```

---

### Post by aonegodman on 2008-01-26
> **tombug said:**
> hm i did step by step 3 times and i still get

```
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'

```

yes i have weather in /user/share/fonts/truetype/myfonts

Did you go to the folder and verify that the fonts - weather.ttf ARE  there?  :)

Be sure to look in /usr/share/fonts/trutype/myfonts.

I'm thinking . . . .     let me know how you're doing and let's take a look at the "weather" section of your conky file.   Please post.

---

### Post by aonegodman on 2008-01-26
> **tombug said:**
> hm i did step by step 3 times and i still get

```
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'

```

yes i have weather in /user/share/fonts/truetype/myfonts

Did you make sure to cache your fonts to make them available?

In Terminal enter:

```

fc-cache -f -v

```

Also be sure to make your weather.pl executable. 

Let us know how you're doing -  :)

---

### Post by jba6511 on 2008-01-27
after playing with the offset settings the script is not updating to the right city. I had it set to buenos aries (sp?) until I got everything aligned and working. I then went back and added my zip and options after making the changes but it does not want to update to my location (it is still showing the forecast for Argentina). Any idea what I am doing wrong? Before, it would automatically download the forecast and who me this in bash before launching conky and it was able to fetch the weather for my zip previously.

conkyrc:
[PHP]# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_hints undecorated,below,skip_taskbar
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 8

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color white

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

#override_utf8_locale no
xftfont Terminus:size=8
xftalpha 0.8

TEXT

${offset 240}${color slate grey}${time %a, } ${color }${time %e %B %G}
${offset 240}${color slate grey}${time %Z,    }${color }${time %H:%M:%S}
${offset 240}${color slate grey}UpTime: ${color }$uptime
${offset 240}${color slate grey}Kern:${color }$kernel
${offset 240}${color slate grey}CPU:${color } $cpu% ${acpitemp}C
${offset 240}${cpugraph 20,130 000000 ffffff}
${offset 240}${color slate grey}Load: ${color }$loadavg
${offset 240}${color slate grey}Processes: ${color }$processes  
${offset 240}${color slate grey}Running:   ${color }$running_processes

${offset 240}${color slate grey}Highest CPU:
${offset 240}${color #ddaa00} ${top name 1}${top_mem cpu 1}
${offset 240}${color lightgrey} ${top name 2}${top cpu 2}
${offset 240}${color lightgrey} ${top name 3}${top cpu 3}
${offset 240}${color lightgrey} ${top name 4}${top cpu 4}

${offset 240}${color slate grey}Highest MEM:
${offset 240}${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${offset 240}${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${offset 240}${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${offset 240}${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${offset 240}${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${offset 240}${membar 3,100}
${offset 240}${color slate grey}SWAP: ${color }$swapperc% $swap/$swapmax
${offset 240}${swapbar 3,100}

${offset 240}${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${offset 240}${fs_bar 3,100 /}
${offset 240}${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${offset 240}${fs_bar 3,100 /home}
${offset 240}${color slate grey}SLACK:  ${color }${fs_free /mnt/slack}/${fs_size /mnt/slack}
${offset 240}${fs_bar 3,100 /mnt/slack}
${offset 240}${color slate grey}NET: 
${offset 240}${color}Up: ${color }${upspeed eth0} k/s
${offset 240}${upspeedgraph eth0 20,130 000000 ffffff}
${offset 240}${color}Down: ${color }${downspeed eth0}k/s${color}
${offset 240}${downspeedgraph eth0 20,130 000000 ffffff}

${voffset -15}${color white}${font weather:size=30}${alignc -110}${execi 14400 perl ~/scripts/weather.pl 27409 f 3dp}$font$color
${color yellow}${alignc -110}${execi 14400 perl ~/scripts/weather.pl 27409 f 3d}
[/PHP]

weather,pl:
[PHP]#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=14400; #time in seconds to update }le if set to 0 don't use }le

$spaces="  "; #spacing between each high low.
$fspaces=" "; #spacing between condition symbols.

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`; #get size of $file

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

if(-e $file && $size){ #does the file exist and is not empty?
        if($size != 0){
                $date=`date -u +%s`; #get current date in seconds
                $created=`stat -c %Y $file`; #get creation date of file in seconds
                $age=$date - $created; #determine age of file
        }
        else{
                $age=$update+1;
        }
}
else{ #if file doesn't exist make it and set to update the file
        `touch $file`;
        $age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
        #obtain the weather forecast and store it in $file
        `wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
        case "cp" { #if current conditions
                while(<FILE>){ #cycle through file
                        if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
                                ($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
                                #do we have current conditions? Then translate into symbol
                                if($cnd){cond_symb($cnd); print "\n"; exit;}
                        }
                }
        }
        case "c" { #if current temp
                while(<FILE>){ #cycle through file
                        if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
                                ($tmp) = /<h3>(-?\d+)/; #save current temp
                                #do we have current temp? Then print
                                if($tmp){print "$1$degree\n"; exit;}
                        }
                }
        }
        case /[1-5]dp$/ { #display the conditions from today through day $days
                $day=(split "p", $what)[0]; #how many days are we looking for
                $flag=0; #set flag for when we find start of conditions
                $count=0; 
                while(<FILE>){
                        if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
                        elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
                                $cnd[$count-1]=$1; #save conditions
                                &cond_symb ($cnd[$count-1]); #translate conditions to symbol
                                #exit;
                        }
                }
        }
        case /[1-5]d$/ { #display the temps from today through day $days
                while(<FILE>){
                        #get the high temp
                        $day=(split "p", $what)[0]; #how many days are we looking for
                        ($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
                        #get the low temp
                        ($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
                        #print the high and low temp for the specified day
                        if($high && $low && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
                }
        }
        case /[1-5]p$/ { #if conditions of specified day
                $day=(split "p", $what)[0]; #what day are we looking for
                $flag=0; #set flag for when we find start of conditions
                $count=0; 
                while(<FILE>){
                        if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
                        elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
                                $cnd=$1; #save conditions
                                &cond_symb ($cnd); #translate conditions to symbol
                                #exit;
                        }
                }
        }
        case /[1-5]$/ { #if temp of specified day 
                while(<FILE>){
                        #get the high temp
                        ($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
                        #get the low temp
                        ($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
                        #print the high and low temp for the specified day
                        if($high && $low && ++$count==$what){print "$high$degree/$low$degree";}
                }
        }
        else { #didn't give proper options
                print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day"
        }
}

print "\n"; # need endline to make things look nice

close FILE;

sub cond_symb { #translates conditions into symbol in weather font
        if ($_ =~ "Partly Cloudy"){$_="c";}
        elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
        elsif ($_ =~ "Cloud"){$_="e";}
        elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
        elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
        elsif ($_ =~ "Rain"){$_="h";}
        elsif ($_ =~ "Shower"){$_="g";}
        print "$_$fspaces";
}
[/PHP]

---

### Post by aonegodman on 2008-01-27
> **jba6511 said:**
> after playing with the offset settings the script is not updating to the right city. I had it set to buenos aries (sp?) until I got everything aligned and working. I then went back and added my zip and options after making the changes but it does not want to update to my location (it is still showing the forecast for Argentina). Any idea what I am doing wrong? Before, it would automatically download the forecast and who me this in bash before launching conky and it was able to fetch the weather for my zip previously.


Change ZIP code to the Weather Code for your city.

Greensboro, NC =  **USNC0280**


Put in this in your scripts at the proper locations as described in FIRST and other posts here.

I was unable to get ZIP to work for me and believe the previous directions should be changed to reflect this necessity.

Remember you must have CURL installed for the CALL to work in your **weather.sh** file. I only mention this because this was a step I had to do.

Good luck with your conky.   :)

---

### Post by jba6511 on 2008-01-27
made the changes and installed CURL and still no luck.

---

### Post by aonegodman on 2008-01-27
> **jba6511 said:**
> made the changes and installed CURL and still no luck.

Ok.  I looked over your two scripts and other than the ZIP code I didn't see any problems with them.

I can't assume what you have or have not done. You have showed us two scripts in your original posts. I must assume that you have the other two required scripts also installed.

If you followed the original post carefully and made the Zip to CODE changes, have the following four scripts in their respective places with naming conventions.

conkymain(conkyrc with weather mods)
weather.pl
weather.xslt
weather.sp( and made it executable)

It should work!   I'll take another look at your scripts above for you. Could you post the others also?

Thanks.  :)

---

### Post by aonegodman on 2008-01-27
Take a look here to make sure you have this folder at location >

/usr/bin/xsltproc


and that you have the html file in your >

/home/<USERNAME>/tmp/weather.html

couple of after thoughts  - :)

---

### Post by Bruce M. on 2008-01-27
> **lvleph said:**
> Okay, i should have said the old V2 way, that is the day by day way. The new test version allows one to print out all 5 days at once, but one can choose to print them one day at a time if one wishes.

After my re-install and restoring my /home folder, I have a lot of work to do, and I'm reading this thread from start to finish (again).  Conky is working, but "blinking every second", I had to download the weather fonts and set them up again.  Don't know why they didn't backup, and my System temps aren't working again.

Work, work and more work to do!

Lets see if I'm reading this correctly:

In the "old" V2 way there are 5 execi font calls, and 5 hi/low calls. Obviously you can trim them back to 4, 3 etc. and space them, colour them and resize them if you wish.

In the "new" V2 way there are 2 execi calls, 1 for fonts and 1 for hi/low.

Spacing via the $fspace and $space adjustments
Sizing via conky commands.

But I don't understand how you can "print" them day by day without adding extra execi calls as I described in what I called "Medium Power" weather conky.

Bruce

---

### Post by Bruce M. on 2008-01-27
> **lvleph said:**
> Bruce, the new script can be ran in the same way the old one was run. He is using the new one, but in the old way.

AHHHHHHHHH!  :popcorn: - **light goes on!**

The new **.PL** file, but calling each day with a seperate CONKY command.

I can be so thick at times.  :)

---

### Post by Bruce M. on 2008-01-27
> **aonegodman said:**
> Yeah, but what I was trying here was to eliminate the little one line clock above the large one. I still wanted the large digital clock display(see my screenshots). But I didn't see a call for tztime that would set the large one. Does that make any sense?

I'll try commenting out and see if large clock works. Next, I'll grab the other *.pl and replace my existing. Thanks.

Don't know if you got an answer from/for this but it's easy:

When you set up Ubuntu, it asked where you were and set the time zone as local time on your machine.

For example:  Buenos Aires is -3 hours from GMT.  This becomes your machines time.

${time %H:%M:%S} <<--- gets the time directly from your machine (your BIG clock)

and, using my machine as an example:

${tztime Canada/Central %H:%M} <<--- tells the time in different time zones around the world by calcualting the difference from your machines time (-3GMT) and the time requested Canada/Central (-4GMT) and displays i hour difference.

12:00 GMT = 09:00 Buenos Aires and 08:00 in Canada/Central

and it follows DST rules too.

Bruce

---

### Post by aonegodman on 2008-01-27
> **Bruce M. said:**
> Don't know if you got an answer from/for this but it's easy:

When you set up Ubuntu, it asked where you were and set the time zone as local time on your machine.

For example:  Buenos Aires is -3 hours from GMT.  This becomes your machines time.

${time %H:%M:%S} <<--- gets the time directly from your machine (your BIG clock)

and, using my machine as an example:

${tztime Canada/Central %H:%M} <<--- tells the time in different time zones around the world by calcualting the difference from your machines time (-3GMT) and the time requested Canada/Central (-4GMT) and displays i hour difference.

12:00 GMT = 09:00 Buenos Aires and 08:00 in Canada/Central

and it follows DST rules too.

Bruce

Oh ok, thanks for that.  I removed both the GMT and the little clock line and it still works, as you have seen, just fine. I just didn't know how.  :)

I've got use to the blue weather icons now - not bad, and 2 execi calls is the way to go.  :)

---

### Post by Bruce M. on 2008-01-27
> **aonegodman said:**
> Oh ok, thanks for that.  I removed both the GMT and the little clock line and it still works, as you have seen, just fine. I just didn't know how.  :)

I've got use to the blue weather icons now - not bad, and 2 execi calls is the way to go.  :)

Well, I mist the bit about time, so I answered today, I've been a little pre-occupied the last week or so, but all is well now.

Yes, much easier on CPU usage. But you can pick any colour you want.  :)

Catch you later.
Bruce

---

### Post by aonegodman on 2008-01-28
> **Bruce M. said:**
> 

Yes, much easier on CPU usage. But you can pick any colour you want.  :)



Yeah, that's the only limitation to the "LOW" script I'm not really happy with.

Wish some way to set it up in other scripts to SET IF color when a condition was returned from weather services without using a seperate execi call for each day.

You know, if the forecast was for rain on a certain day then the cloud font would be changed to gray automatically by the - oh I don't know, maybe the weather.pl  *cloud filter* routine.  :lolflag:

Hey it's 3AM in the morning here, can't sleep and here I am . . .

:)

---

### Post by jba6511 on 2008-01-28
I only have the weather.pl script and the additions I made to conkyrc. Which pages are the other two scripts that are needed on? I ran through the thread but must have missed them.

---

### Post by aonegodman on 2008-01-28
> **jba6511 said:**
> I only have the weather.pl script and the additions I made to conkyrc. Which pages are the other two scripts that are needed on? I ran through the thread but must have missed them.

[SIZE="3"]I'm sorry, I have been back and forth through these conky files so much I forget sometimes which threads are where. Please forgive me.

Now take a look at the following post by my associate, [SIZE="4"]the one[/SIZE], [SIZE="5"]the only[/SIZE]

 [SIZE="6"]**Bruce "conkyman" M.**[/SIZE][/SIZE]  :guitar:   My mentor.   :)


[http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489](http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489)

If you want to add [COLOR="Green"]Gmail notification[/COLOR], ect

then check out the following link by the originator of this thread and the [COLOR="Red"]"real deal"[/COLOR] programmer  [COLOR="Green"]**lvleph**[/COLOR]

[http://ubuntuforums.org/showpost.php?p=4219577&postcount=1](http://ubuntuforums.org/showpost.php?p=4219577&postcount=1)

---

### Post by Bruce M. on 2008-01-28
> **aonegodman said:**
> [SIZE="3"]Now take a look at the following post by my associate, [SIZE="4"]the one[/SIZE], [SIZE="5"]the only[/SIZE]

 [SIZE="6"]**Bruce "conkyman" M.**[/SIZE][/SIZE]  :guitar:   My mentor.   :)

You've got to be kidding.  I'll I did was pass on stuff I learned here and there, and help you get past one of ***MY*** mistakes, and that took like all day, posing every few minutes.

I can't stop laughing here, thanks for that, *partner*, I needed it today!

---

### Post by noremac on 2008-01-29
Great script, but please excuse me if I didn't see a solution:

 [edit] Nevermind, I found the solution on page 3 and 4 of this thread. Just gonna leave this here to help any in the future. [/edit]

For some reason I have  a capital A with a small line above it between the temperature and the degree symbol. Its like this on every temperature it displays. It causes the temperatures to be much longer, thus all the forecast temps don't show up on my 200pixel wide conky :(

Any known solution or reason it'd do this?
Thanks,
-Cameron

---

### Post by Bruce M. on 2008-01-29
> **aonegodman said:**
> Yeah, that's the only limitation to the "LOW" script I'm not really happy with.

Wish some way to set it up in other scripts to SET IF color when a condition was returned from weather services without using a seperate execi call for each day.

You know, if the forecast was for rain on a certain day then the cloud font would be changed to gray automatically by the - oh I don't know, maybe the weather.pl  *cloud filter* routine.  :lolflag:

I'm more than satisfied.  Imagine someone who changes backgrounds a lot, (anybody we know?) a nice white fluffy cloud would disappear on a light background, or a black thunder storm cloud would look great on a black background too.


> **aonegodman said:**
> Hey it's 3AM in the morning here, can't sleep and here I am . . .

:)

It was a darned good idea too, for 3am  :)

---

### Post by Bruce M. on 2008-01-29
WoW! Check [this one]("http://ubuntuforums.org/showpost.php?p=4228240&postcount=1673") out, the code is in the post one above #1672.  :)

---

### Post by lvleph on 2008-01-29
> **noremac said:**
> Great script, but please excuse me if I didn't see a solution:

 [edit] Nevermind, I found the solution on page 3 and 4 of this thread. Just gonna leave this here to help any in the future. [/edit]

For some reason I have  a capital A with a small line above it between the temperature and the degree symbol. Its like this on every temperature it displays. It causes the temperatures to be much longer, thus all the forecast temps don't show up on my 200pixel wide conky :(

Any known solution or reason it'd do this?
Thanks,
-Cameron

It was also note 1 in the instructions.

---

### Post by Cammy on 2008-01-29
> **Bruce M. said:**
> WoW! Check [this one]("http://ubuntuforums.org/showpost.php?p=4228240&postcount=1673") out, the code is in the post one above #1672.  :)

HEY!   I need to look at that guy's conky when I get home.  He has the DAYS above the forecasts!!!!

---

### Post by lvleph on 2008-01-29
> **Cammy said:**
> HEY!   I need to look at that guy's conky when I get home.  He has the DAYS above the forecasts!!!!

He rewrote the script to include that option. It was something I was planning on doing. I just wish that when someone made those additions, they would share them.

---

### Post by Cammy on 2008-01-29
> **lvleph said:**
> He rewrote the script to include that option.
The weather.pl?


> **lvleph said:**
> I just wish that when someone made those additions, they would share them.
Agreed.  It's the way open source software is supposed to work.

---

### Post by lvleph on 2008-01-29
Yes, he added some options to weather.pl. I pm him and asked him to post his additions here.

---

### Post by Bruce M. on 2008-01-29
> **lvleph said:**
> Yes, he added some options to weather.pl. I pm him and asked him to post his additions here.

Not only that, he asked if someone could help him "clean it up".  :)
Have to share to do that.  :)

---

### Post by aonegodman on 2008-01-29
> **Bruce M. said:**
> I'm more than satisfied.  Imagine someone who changes backgrounds a lot, (anybody we know?) a nice white fluffy cloud would disappear on a light background, or a black thunder storm cloud would look great on a black background too.




It was a darned good idea too, for 3am  :)

:lolflag:   Got me there. You're right.

---

### Post by belzebubek on 2008-01-29
Hi folks, any ideas? 

my weather.pl


```
#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

$spaces="     "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`; #get size of $file

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

if(-e $file && $size){ #does the file exist and is not empty?
	if($size != 0){
		$date=`date -u +%s`; #get current date in seconds
		$created=`stat -c %Y $file`; #get creation date of file in seconds
		$age=$date - $created; #determine age of file
	}
	else{
		$age=$update+1;
	}
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "cp" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d$/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tcp displays current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day"
	}
}

print "\n"; # need endline to make things look nice

close FILE;

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_$fspaces";
}
```


and conkyrc

```
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl /home/marcin/Dokumenty/scripts/weather.pl PLXX0040 c 5dp}${font}$color
${offset 18}${execi 3600 perl /home/marcin/Dokumenty/scripts/weather.pl PLXX0040 c 5d}
```

---

### Post by aonegodman on 2008-01-29
> **Bruce M. said:**
> WoW! Check [this one]("http://ubuntuforums.org/showpost.php?p=4228240&postcount=1673") out, the code is in the post one above #1672.  :)

Nice concept for an ALL WEATHER desktop script.  Looks good. I like the large current conditions on top.

What scares me is I have messed with this stuff so much lately, that just looking at it I begin to formulate in my mind just how it was done. Too much Ubuntu and Conky.

< smilie with blood shot eyes goes here >

:lol:

---

### Post by pabelanger on 2008-01-29
> **tombug said:**
> hm i did step by step 3 times and i still get

```
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'

```

yes i have weather in /usr/share/fonts/truetype/myfonts

Same thing for me.  My weather.ttf exists in /usr/share/fonts/truetype/myfonts, I have ran fc-cache -f -v, and still no luck.

PB

---

### Post by Bruce M. on 2008-01-29
> **belzebubek said:**
> Hi folks, any ideas? 

and conkyrc

```
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl /home/marcin/Dokumenty/scripts/weather.pl PLXX0040 c 5dp}${font}$color
${offset 18}${execi 3600 perl /home/marcin/Dokumenty/scripts/weather.pl PLXX0040 c 5d}
```

I'm no programmer but, Line 1 of your code:
```
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl /home/marcin/Dokumenty/scripts/weather.pl PLXX0040 c 5dp}${font}$color

```

ends with the closing variables: **${font}$color** and no starting variables.  Delete these and see what happens.

---

### Post by pabelanger on 2008-01-29
> **tombug said:**
> hm i did step by step 3 times and i still get

```
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'
Conky: can't load font 'weather:size=45'

```

yes i have weather in /user/share/fonts/truetype/myfonts

Figured it out

```
use_xft yes
```

in your .conkyrc file

---

### Post by LazarusHC on 2008-01-30
> **lvleph said:**
> Yes, he added some options to weather.pl. I pm him and asked him to post his additions here.

Okay, here it is.  I'm still trying to make a few more tweeks, but this is what I have for now.  I don't really know python, I made these changes with a lot of copy and pasting, a little reverse engineering, and a little bit of guess work.  So, if there's a better way to do what I did, I'd be happy to hear it.  

That being said, here's my altered script.

```
#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

$spaces="       "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$tspaces="   ";

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`; #get size of $file

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

if(-e $file && $size){ #does the file exist and is not empty?
	if($size != 0){
		$date=`date -u +%s`; #get current date in seconds
		$created=`stat -c %Y $file`; #get creation date of file in seconds
		$age=$date - $created; #determine age of file
	}
	else{
		$age=$update+1;
	}
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "t" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "l" { #if list
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){print "Feels like:   $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:         $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]t$/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<table>\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnt[$count-1]=$1; #save conditions
				&cont_symb ($cnt[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d$/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tt displays current conditions
\t\tcp displays current conditions symbol
\t\tl displays list of current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day
\t\t[1-5]t displays the day for the coresponding condition/temp 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day"
	}
}

print "\n"; # need endline to make things look nice

close FILE;

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_$fspaces";
}

sub cont_symb { #deletes un-needed characters for conditions titles
	if ($_ =~ "Today"){$_="Today   ";}
	elsif ($_ =~ "Tonight"){$_="Tonight ";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="Thu     ";}
	elsif ($_ =~ "Fri"){$_="Fri     ";}
	elsif ($_ =~ "Sat"){$_="Sat     ";}
	elsif ($_ =~ "Sun"){$_="sun     ";}
	elsif ($_ =~ "Mon"){$_="Mon     ";}
	elsif ($_ =~ "Tue"){$_="Tue     ";}
	elsif ($_ =~ "Wed"){$_="Wed     ";}
	print "$_$tspaces";
}
```

Here's my conkyrc.  I'm still tweeking this, too.

```
${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS
${voffset -9}$hr $color
${font Arial:size=15}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c t}
${alignr 66}${voffset -15}${font Arial:size=18}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c c}${font weather:size=100}${offset -28}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c cp}$font
${font Arial:size=10}${voffset -88}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c l}$font

${voffset 18}${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${alignc}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c 5t}
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c 5dp}${font}$color
${alignc}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c 5d}
${voffset 10}${texeci 1800 cat /tmp/weather.html | grep '<li><strong>' | sed 's/<\/li>/\n/; s/<li><strong>//; s/<\/strong>//' | ~/scripts/wordwrap -w 50}
```

And here's the wordwrap script.

```
:
##########################################################################
# Shellscript:	wordwrap - wrap lines on word boundaries
# Author     :	Heiner Steven <heiner.steven@odn.de>
# Date       :	2001-12-10
# Requires   :	
# Category   :	Text Utilities
# SCCS-Id.   :	@(#) wordwrap	1.4 04/09/24
##########################################################################
# Description
#	A very simple text formatting program. The input is read
#	word by word.  All words are joined using a space (ASCII
#	32) character. If "-j" was specified, each line is
#	filled up to the maximum line length, or the next empty
#	line before it is printed. Each continued line can be
#	offset by a number of blanks.
#
# Note
#    o	Leading whitespace is ignored
#    o	An AWK program actually formats the input. It is written in
#	a way to be portable to a wide range of AWK dialects.
#    o  thanks for Samus-Aran for suggesting the "-l" option
#
# Caveats
#    o	Should have an option for keeping whitespace inbetween words
##########################################################################

PN=`basename "$0"`			# Program name
VER='1.4'

# Uncomment the following line to disable the search for the fastest AWK
#: ${AWK:=awk}

DEFWIDTH=72				# Default line length
DEFOFFSET=0				# Default continued line offset
DEFMARGIN=0				# Default left margin

Usage () {
    echo >&2 "$PN - wrap lines on word boundaries, $VER
usage: $PN [-j] [-w width] [-o offset] [-l margin] [file ...]
    -j  join multiple lines up to the maximum line length
    -l  left margin (default $DEFMARGIN)
    -o  offset of continued lines (default $DEFOFFSET)
    -w  max. line width (default is $DEFWIDTH characters)"
    exit 1
}

Msg () {
    for MsgLine
    do echo "$PN: $MsgLine" >&2
    done
}

Fatal () { Msg "$@"; exit 1; }

##########################################################################
# searchprog - search program using search PATH
# usage: searchprog program
##########################################################################

searchprog () {
    _search=$1; shift

    for _dir in `echo "$PATH" | sed "s/^:/.:/;s/:\$/:./;s/::/:.:/g;s/:/ /g"`
    do
        [ -x "$_dir/$_search" ] || continue
        echo "$_dir/$_search"
        return 0
    done

    return 1
}

# isint - is argument a valid integer number?
isint () {
    case "$1" in
    	*[!0-9]*)   return 1;;
	*)	    return 0;;
    esac
}

set -- `getopt :hjl:o:w: "$@"` || Usage
[ $# -lt 1 ] && Usage			# "getopt" detected an error

# Search for an AWK implementation, prefer the fastest one
: ${AWK:=`searchprog mawk || searchprog gawk || searchprog nawk || echo awk`}

LineWidth=
JoinLines=false
LeftMargin=
while [ $# -gt 0 ]
do
    case "$1" in
	-j)	JoinLines=true;;
	-l)	isint "$2" || Fatal "invalid margin: $2"
		LeftMargin=$2; shift;;
	-o)	isint "$2" || Fatal "invalid offset: $2"
		LineOffset=$2; shift;;
	-w)	isint "$2" || Fatal "invalid line width: $2"
		LineWidth=$2; shift;;
	--)	shift; break;;
	-h)	Usage;;
	-*)	Usage;;
	*)	break;;			# First file name
    esac
    shift
done

: ${LineWidth:=$DEFWIDTH}
: ${LineOffset:=$DEFOFFSET}
: ${LeftMargin:=$DEFMARGIN}

$AWK '
    BEGIN {
	WORDSEP = " "
	WORDSEPLEN = length (WORDSEP)
	maxwidth = '"$LineWidth"'
	if ( "'"$JoinLines"'" == "true" ) joinlines = 1; else joinlines = 0;
	line = ""
	offset = '"$LineOffset"'
	margin = '"$LeftMargin"'
	if ( offset >= 1 ) indent = sprintf ("%*s", offset, " ")
	if ( margin >= 1 ) leftmargin = sprintf ("%*s", margin, "")
    }
    {
    	# Special handling: preserve leading whitespace characters
	if ( line == "" ) {
	    for ( i=1; i<length($0); ++i ) {
		c = substr ($0, i, 1)
		if ( c != " " && c != "	" ) break
	    }
	    if ( i > 1 ) line = substr ($0, 1, i-1)
	}

	for ( i=1; i<=NF; ++i ) {
	    newlen = length (line) + length ($i)
	    if ( line != "" ) newlen += WORDSEPLEN
	    if ( newlen > maxwidth ) {
	        print leftmargin line
		line = indent $i
	    } else {
		if ( line != "" ) line = line WORDSEP
		line = line $i
	    }
	}

	# No joining of lines: print the current line immediately

	if ( !joinlines || NF == 0 ) {
	    print leftmargin line
	    if ( line != "" && NF == 0 ) print ""	# preserve empty line
	    line = ""
	}
    }
    END {
	if ( line != "" ) {
	    print leftmargin line
	}
    }
' "$@"
```

I'm off to bed.

---

### Post by lvleph on 2008-01-30
> **LazarusHC said:**
> Okay, here it is.  I'm still trying to make a few more tweeks, but this is what I have for now.  I don't really know python, I made these changes with a lot of copy and pasting, a little reverse engineering, and a little bit of guess work.  So, if there's a better way to do what I did, I'd be happy to hear it.  

That being said, here's my altered script.

```
#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

$spaces="       "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$tspaces="   ";

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

$size=`stat -t $file -c %s`; #get size of $file

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

if(-e $file && $size){ #does the file exist and is not empty?
	if($size != 0){
		$date=`date -u +%s`; #get current date in seconds
		$created=`stat -c %Y $file`; #get creation date of file in seconds
		$age=$date - $created; #determine age of file
	}
	else{
		$age=$update+1;
	}
}
else{ #if file doesn't exist make it and set to update the file
	`touch $file`;
	$age=$update+1;
}

if ($age>=$update){ #only get a new file every hour
	#obtain the weather forecast and store it in $file
	`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
}

open(FILE, "$file") or die "Cannot open file $file: $1\n";

$count=0; #set count so we can match proper day
$days=(split /d/, $what)[0]; #get number of days

switch($what){ #determine what user wants
	case "t" { #if current conditions
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "l" { #if list
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){print "Feels like:   $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:         $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "c" { #if current temp
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]t$/ { #display the conditions from today through day $days
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<table>\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnt[$count-1]=$1; #save conditions
				&cont_symb ($cnt[$count-1]); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]d$/ { #display the temps from today through day $days
		while(<FILE>){
			#get the high temp
			$day=(split "p", $what)[0]; #how many days are we looking for
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		$day=(split "p", $what)[0]; #what day are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
				#exit;
			}
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>
weather.pl <citycode> <system> <option>
\t<citycode> - weather.com city code
\t<system> - c for metric or f for imperial
\t<option> - Only one option can be entered at a time
\t\tt displays current conditions
\t\tcp displays current conditions symbol
\t\tl displays list of current conditions
\t\tc displays current temp in chosen system
\t\t[1-5]dp displays conditions for days up to specified day
\t\t[1-5]d displays high/low temp in chosen system up to specified day
\t\t[1-5]t displays the day for the coresponding condition/temp 
\t\t[1-5]p displays conditions for specified day
\t\t[1-5] displays high/low temp in chosen system for specified day"
	}
}

print "\n"; # need endline to make things look nice

close FILE;

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_$fspaces";
}

sub cont_symb { #deletes un-needed characters for conditions titles
	if ($_ =~ "Today"){$_="Today   ";}
	elsif ($_ =~ "Tonight"){$_="Tonight ";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="Thu     ";}
	elsif ($_ =~ "Fri"){$_="Fri     ";}
	elsif ($_ =~ "Sat"){$_="Sat     ";}
	elsif ($_ =~ "Sun"){$_="sun     ";}
	elsif ($_ =~ "Mon"){$_="Mon     ";}
	elsif ($_ =~ "Tue"){$_="Tue     ";}
	elsif ($_ =~ "Wed"){$_="Wed     ";}
	print "$_$tspaces";
}
```

Here's my conkyrc.  I'm still tweeking this, too.

```
${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS
${voffset -9}$hr $color
${font Arial:size=15}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c t}
${alignr 66}${voffset -15}${font Arial:size=18}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c c}${font weather:size=100}${offset -28}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c cp}$font
${font Arial:size=10}${voffset -88}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c l}$font

${voffset 18}${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${alignc}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c 5t}
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c 5dp}${font}$color
${alignc}${execi 3600 perl ~/scripts/weather.pl JAXX0085 c 5d}
${voffset 10}${texeci 1800 cat /tmp/weather.html | grep '<li><strong>' | sed 's/<\/li>/\n/; s/<li><strong>//; s/<\/strong>//' | ~/scripts/wordwrap -w 50}
```

And here's the wordwrap script.

```
:
##########################################################################
# Shellscript:	wordwrap - wrap lines on word boundaries
# Author     :	Heiner Steven <heiner.steven@odn.de>
# Date       :	2001-12-10
# Requires   :	
# Category   :	Text Utilities
# SCCS-Id.   :	@(#) wordwrap	1.4 04/09/24
##########################################################################
# Description
#	A very simple text formatting program. The input is read
#	word by word.  All words are joined using a space (ASCII
#	32) character. If "-j" was specified, each line is
#	filled up to the maximum line length, or the next empty
#	line before it is printed. Each continued line can be
#	offset by a number of blanks.
#
# Note
#    o	Leading whitespace is ignored
#    o	An AWK program actually formats the input. It is written in
#	a way to be portable to a wide range of AWK dialects.
#    o  thanks for Samus-Aran for suggesting the "-l" option
#
# Caveats
#    o	Should have an option for keeping whitespace inbetween words
##########################################################################

PN=`basename "$0"`			# Program name
VER='1.4'

# Uncomment the following line to disable the search for the fastest AWK
#: ${AWK:=awk}

DEFWIDTH=72				# Default line length
DEFOFFSET=0				# Default continued line offset
DEFMARGIN=0				# Default left margin

Usage () {
    echo >&2 "$PN - wrap lines on word boundaries, $VER
usage: $PN [-j] [-w width] [-o offset] [-l margin] [file ...]
    -j  join multiple lines up to the maximum line length
    -l  left margin (default $DEFMARGIN)
    -o  offset of continued lines (default $DEFOFFSET)
    -w  max. line width (default is $DEFWIDTH characters)"
    exit 1
}

Msg () {
    for MsgLine
    do echo "$PN: $MsgLine" >&2
    done
}

Fatal () { Msg "$@"; exit 1; }

##########################################################################
# searchprog - search program using search PATH
# usage: searchprog program
##########################################################################

searchprog () {
    _search=$1; shift

    for _dir in `echo "$PATH" | sed "s/^:/.:/;s/:\$/:./;s/::/:.:/g;s/:/ /g"`
    do
        [ -x "$_dir/$_search" ] || continue
        echo "$_dir/$_search"
        return 0
    done

    return 1
}

# isint - is argument a valid integer number?
isint () {
    case "$1" in
    	*[!0-9]*)   return 1;;
	*)	    return 0;;
    esac
}

set -- `getopt :hjl:o:w: "$@"` || Usage
[ $# -lt 1 ] && Usage			# "getopt" detected an error

# Search for an AWK implementation, prefer the fastest one
: ${AWK:=`searchprog mawk || searchprog gawk || searchprog nawk || echo awk`}

LineWidth=
JoinLines=false
LeftMargin=
while [ $# -gt 0 ]
do
    case "$1" in
	-j)	JoinLines=true;;
	-l)	isint "$2" || Fatal "invalid margin: $2"
		LeftMargin=$2; shift;;
	-o)	isint "$2" || Fatal "invalid offset: $2"
		LineOffset=$2; shift;;
	-w)	isint "$2" || Fatal "invalid line width: $2"
		LineWidth=$2; shift;;
	--)	shift; break;;
	-h)	Usage;;
	-*)	Usage;;
	*)	break;;			# First file name
    esac
    shift
done

: ${LineWidth:=$DEFWIDTH}
: ${LineOffset:=$DEFOFFSET}
: ${LeftMargin:=$DEFMARGIN}

$AWK '
    BEGIN {
	WORDSEP = " "
	WORDSEPLEN = length (WORDSEP)
	maxwidth = '"$LineWidth"'
	if ( "'"$JoinLines"'" == "true" ) joinlines = 1; else joinlines = 0;
	line = ""
	offset = '"$LineOffset"'
	margin = '"$LeftMargin"'
	if ( offset >= 1 ) indent = sprintf ("%*s", offset, " ")
	if ( margin >= 1 ) leftmargin = sprintf ("%*s", margin, "")
    }
    {
    	# Special handling: preserve leading whitespace characters
	if ( line == "" ) {
	    for ( i=1; i<length($0); ++i ) {
		c = substr ($0, i, 1)
		if ( c != " " && c != "	" ) break
	    }
	    if ( i > 1 ) line = substr ($0, 1, i-1)
	}

	for ( i=1; i<=NF; ++i ) {
	    newlen = length (line) + length ($i)
	    if ( line != "" ) newlen += WORDSEPLEN
	    if ( newlen > maxwidth ) {
	        print leftmargin line
		line = indent $i
	    } else {
		if ( line != "" ) line = line WORDSEP
		line = line $i
	    }
	}

	# No joining of lines: print the current line immediately

	if ( !joinlines || NF == 0 ) {
	    print leftmargin line
	    if ( line != "" && NF == 0 ) print ""	# preserve empty line
	    line = ""
	}
    }
    END {
	if ( line != "" ) {
	    print leftmargin line
	}
    }
' "$@"
```

I'm off to bed.

By the way it is perl. That will help you when looking up info on how to do something with the language. I will go through the code and optimize some things and then I will release it in the directions.

---

### Post by Cammy on 2008-01-30
**@lvleph:** In your original weather script, are the 1-5 days ahead for today, tomorrow, the next day, etc, or are they for today, tonight, tomorrow, etc?

I was assuming the 4 weather symbols on my conky were for the next four days, then noticed that Lazarus's script had one for "tonight", though he may have added that.

I'm just trying to get the names of the days above the clouds, but don't want to label one as tomorrow when it's really tonight.

---

### Post by lvleph on 2008-01-30
It is today, tomorrow, etc.

---

### Post by lvleph on 2008-01-30
The script right above yours has the days already done.

---

### Post by Cammy on 2008-01-30
> **lvleph said:**
> It is today, tomorrow, etc.

Awesome! Can't wait to get home to fiddle!

---

### Post by Bruce M. on 2008-01-30
> **lvleph said:**
> The script right above yours has the days already done.

But can that function (days) be used in the Low Power **.PL** script?


For example:

```
 weather font line
 days line
 hi/lows line
```

I'm trying but can make heads nor tails out of it.  :(

---

### Post by Bruce M. on 2008-01-30
```
sh: /home/bruloo/scripts/wordwrap: not found
```

But it is there and I've done:

```
bruloo@The-Team:~$ sudo chmod a+x ~/scripts/wordwrap.sh
bruloo@The-Team:~$ sudo chmod a+x ~/scripts/w-days.pl
```

```
TEXT
${color white}$hr
${voffset -3}$alignc CURRENT CONDITIONS
${voffset -9}$hr $color
${font Arial:size=15}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c t}${alignr 66}${font Arial:size=18}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c c}${font weather:size=100}${offset -28}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c cp}$font
${font Arial:size=10}${voffset -88}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c l}$font

${voffset 18}$hr
${voffset -3}$alignc 5 DAY FORECAST
${voffset -9}$hr $color
${offset 10}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c 5t}
${voffset -5}${font weather:size=45}${alignc}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c 5dp}${font}$color
${offset 25}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c 5d}
${voffset 10}${texeci 1800 cat /tmp/weather.html | grep '<li><strong>' | sed 's/<\/li>/\n/; s/<li><strong>//; s/<\/strong>//' | ~/scripts/wordwrap -w 50}
```

---

### Post by Crinos512 on 2008-01-30
> **Bruce M. said:**
> ```
sh: /home/bruloo/scripts/wordwrap: not found
```

But it is there and I've done:

```
bruloo@The-Team:~$ sudo chmod a+x ~/scripts/wordwrap.sh
bruloo@The-Team:~$ sudo chmod a+x ~/scripts/w-days.pl
```

Here's yer fix....change your last line of yer .conkyrc to:

[COLOR="Blue"]${voffset 10}${texeci 1800 cat /tmp/weather.html | grep '<li><strong>' | sed 's/<\/li>/\n/; s/<li><strong>//; s/<\/strong>//' | ~/scripts/[/COLOR][COLOR="Red"]**wordwrap.sh**[/COLOR][COLOR="#0000ff"]  -w 50}[/COLOR]

---

### Post by LazarusHC on 2008-01-30
> **Cammy said:**
> **@lvleph:** In your original weather script, are the 1-5 days ahead for today, tomorrow, the next day, etc, or are they for today, tonight, tomorrow, etc?

I was assuming the 4 weather symbols on my conky were for the next four days, then noticed that Lazarus's script had one for "tonight", though he may have added that.

I'm just trying to get the names of the days above the clouds, but don't want to label one as tomorrow when it's really tonight.

Actually, it changes depending on the time of day and, of coarse, with the day of the week.  Which is why I added it to weather.pl, and not right into conkyrc itself.  For example, if it were 4pm on sat, it would say "Tonight  Tomorrow Mon Tue Wed,"  but if it were 8am on Tue, it would say "Today Tomorrow Thu Fri Sat,"  and so on.

---

### Post by LazarusHC on 2008-01-30
> **lvleph said:**
> By the way it is perl. That will help you when looking up info on how to do something with the language. I will go through the code and optimize some things and then I will release it in the directions.

Perl, eh?  Hmmm... I think I just revealed the full extent of my ignorance.  Oh well.. Maybe that's why nothing I looked up seemed to work.  LOL  Maybe I can actually make the additions I was hopping to, instead of just hacking away at it like I have been.  LOL

---

### Post by lvleph on 2008-01-30
The days should work the way you have it. I need to look over the script still, so don't take my word for it. The wrap, I am not sure the problem.

---

### Post by Bruce M. on 2008-01-30
> **Crinos512 said:**
> Here's yer fix....change your last line of yer .conkyrc to:

[COLOR="Blue"]${voffset 10}${texeci 1800 cat /tmp/weather.html | grep '<li><strong>' | sed 's/<\/li>/\n/; s/<li><strong>//; s/<\/strong>//' | ~/scripts/[/COLOR][COLOR="Red"]**wordwrap.sh**[/COLOR][COLOR="#0000ff"]  -w 50}[/COLOR]

Oh ... I just cut and pasted it, I thought it was a .sh file, guess not.

Nope, still doesn't work :(

---

### Post by Crinos512 on 2008-01-30
can you verify that you have a file named wordwrap.sh in your ~/scripts/ directory?

---

### Post by lvleph on 2008-01-30
Wait until tomorrow and I will have a new script for you and you won't need the wrap script.

---

### Post by Crinos512 on 2008-01-30
> **lvleph said:**
> Wait until tomorrow and I will have a new script for you and you won't need the wrap script.

Awesome, I'll use the new (v3.0?) script, but I think I will keep the wordwrap script too, you never know when it'll come in handy. :D

:guitar:

---

### Post by LazarusHC on 2008-01-31
> **Bruce M. said:**
> Oh ... I just cut and pasted it, I thought it was a .sh file, guess not.

Nope, still doesn't work :(

Okay, for some reason, it doesn't work if you name it *.sh.  I have no idea why, but you have to name is simply "wordwrap."  Mine works perfectly, so I tried renaming it with the .sh extension (with a similar renaming in conkyrc, of coarse), and it no longer worked.  In any case, hopefully the file can be ported to perl, and we won't need to use the script at all. 

Hope this helps!

---

### Post by Bruce M. on 2008-01-31
> **Crinos512 said:**
> can you verify that you have a file named wordwrap.sh in your ~/scripts/ directory?

Yes I do and it is executable.

I got it working ... {hanging head in shame} I had an error in the **PL** file, seems I pasted some text from somewhere else in there as well.

**DUH!**

---

### Post by Bruce M. on 2008-01-31
> **LazarusHC said:**
> Okay, for some reason, it doesn't work if you name it *.sh.  I have no idea why, but you have to name is simply "wordwrap."  Mine works perfectly, so I tried renaming it with the .sh extension (with a similar renaming in conkyrc, of coarse), and it no longer worked.  In any case, hopefully the file can be ported to perl, and we won't need to use the script at all. 

Hope this helps!

See my post above, it works fine with the **SH** file. I goofed up else where.
But all in all, your script is very clever, I like it.

Bruce

**EDIT:**  I named it **.sh** because the error I was getting in Terminal read:

```
sh: error with wordwrap line ......
```

So I figured; Oh, it's an **SH** file, and renamed it.

---

### Post by lvleph on 2008-01-31
Okay I have finished the new version. It is different in its usage so read that over.
```
weather.pl <citycode> <system> <option>
        <citycode> - weather.com city code
        <system> - c for metric or f for imperial
        <option> - Only one option can be entered at a time
                c displays current conditions
                w displays list of current conditions
                cp displays current conditions symbol
                t displays current temp in chosen system
                [1-5]d displays the days up to specified day
                [1-5]dp displays condition symbol for days up to specified day
                [1-5]t displays high/low temp in chosen system up to specified day
                [1-7]w displays the weather in words up number specified
                [1-5]p displays conditions for specified day
                [1-5] displays high/low temp in chosen system for specified day
```

For the [1-7]w option, which will display the weather in words up to the number requested there are new varibles. $Text::Wrap::columns (line 20) is used for word wraps and will tell the script to start new line after specified column. There is also a two other new variables for formatting those word wraps; $initial_tab and $subsequent_tab (line 22 and line 23). These variables place a tab in the beginning of the line.

For displaying the days there is the new option [1-5]d. This will display the days corresponding to the conditions up to the specified day. Spacing is controlled by the variable $dspaces (line 19).

To display the list of current conditions use the option w.

To display the current conditions use the option c. 

I have not done much playing around with the formatting so have fun.

```
#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

$spaces="     "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="    ";
$Text::Wrap::columns = 55;

$initial_tab=""; #tab before first line in weather output
$subsequent_tab="\t"; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Feels like:  $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			my $day=(split "t", $what)[0]; #how many days are we looking for
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size != 0){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_$fspaces";
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Today ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	print "$_$dspaces";
}
```

This is still beta and I am still going to mess around with it, but it should be working.

---

### Post by kenshin_i on 2008-01-31
I have some problem with condition "wintry mix", it just gave out some random wather fonts
So for now I just added a line in sub cond_symb:

```

elsif ($_ =~ "Wintry Mix"){$_="hj";}

```

Anyone have better solution?  I do not know which font to use, so settle with two fonts for "Wintry Mix" condition.

---

### Post by lvleph on 2008-01-31
I just added wintry mix to display snow. If I knew how to write fonts I would make one just for this, but I don't.

The following is the newest code, and so usage is different refer to my post two above this one.

```
#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

$spaces="     "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="    ";
$Text::Wrap::columns = 55;

$initial_tab=""; #tab before first line in weather output
$subsequent_tab="\t"; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Feels like:  $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		$day=(split "p", $what)[0]; #how many days are we looking for
		$flag=0; #set flag for when we find start of conditions
		$count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			my $day=(split "t", $what)[0]; #how many days are we looking for
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size != 0){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	print "$_$fspaces";
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Today ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	print "$_$dspaces";
}
```

---

### Post by Bruce M. on 2008-01-31
My brand new **Conky 5 Day Forcast (v3.0)** in development.

[CENTER][[IMG]http://img218.imageshack.us/img218/1567/new5dayxj8.th.png[/IMG]](http://img218.imageshack.us/my.php?image=new5dayxj8.png)[/CENTER]

**[CENTER]Look at that: Spanish!  I love it![/CENTER]**

Above the [COLOR="Red"]**red line**[/COLOR] is Conky 5 day Forcast (V2.0) and below is Conky 5 day Forcast (V3.0)

Conky code:
```

${color orange}WEATHER: ${color cyan}${hr 1}$color
${color cyan}Lat: ${color orange}34°35'00"S   ${color cyan}Long: ${color orange}58°21'00"W ${alignr} ${color cyan}Alt: ${color orange}25 m$color
${color yellow}${execi 600 ~/scripts/myweather.sh ARBA0009}$color

${color cyan}${hr 1} $color

${voffset +1}${color cyan}${font weather:size=30}${alignc -2}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}$font$color
${color yellow}${alignc}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5d}

${color red}${hr 10} $color

${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5d}
${color cyan}${font weather:size=30}${alignc -2}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}$font$color
${color yellow}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5t}$color

${color cyan}${hr 1} $color

```

Lines I modified in the **.PL** file:

Lines: 17-20
```

$spaces="  "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="  ";
$Text::Wrap::columns = 55;

```
Lines: 220-230
```

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="   Hoy  ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Mañana";}
	elsif ($_ =~ "Thu"){$_="   Jue  ";}
	elsif ($_ =~ "Fri"){$_="   Vie  ";}
	elsif ($_ =~ "Sat"){$_="   Sab  ";}
	elsif ($_ =~ "Sun"){$_="   Dom  ";}
	elsif ($_ =~ "Mon"){$_="   Lun  ";}
	elsif ($_ =~ "Tue"){$_="   Mar  ";}
	elsif ($_ =~ "Wed"){$_="   Mie  ";}

```

**EDIT:** Code Update: It just popped into "Tonight" ... so I used Night = Noche
```

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="   Hoy  ";}
	elsif ($_ =~ "Tonight"){$_=" Noche ";}
	elsif ($_ =~ "Tomorrow"){$_="Mañana";}
	elsif ($_ =~ "Thu"){$_="   Jue  ";}
	elsif ($_ =~ "Fri"){$_="   Vie  ";}
	elsif ($_ =~ "Sat"){$_="   Sab  ";}
	elsif ($_ =~ "Sun"){$_="   Dom  ";}
	elsif ($_ =~ "Mon"){$_="   Lun  ";}
	elsif ($_ =~ "Tue"){$_="   Mar  ";}
	elsif ($_ =~ "Wed"){$_="   Mie  ";}

```

I chose to stay with the old style conky weather for the conditions today because it gives them to me in Celsius rather than Fahrenheit.  Even though I call for Celsius in the **.pl** file, the 5 day forecast conditions are in Fahrenheit. 

[CENTER][SIZE="4"]**Thank you lvleph and LazarusHC**[/SIZE][/CENTER]

Now it looks like this attachment.

---

### Post by Crinos512 on 2008-01-31
How about changing lines 151-160 to read
 
```

[COLOR="Blue"]	case /[1-5]$/ { #if temp of specified day
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree[COLOR="Red"] $system[/COLOR]\n";}
		}[/COLOR]

```

...thus when you request Celcius, it shows in yer Conky

---

### Post by lvleph on 2008-01-31
> **Crinos512 said:**
> How about changing lines 151-160 to read
 
```

[COLOR="Blue"]	case /[1-5]$/ { #if temp of specified day
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree[COLOR="Red"] $system[/COLOR]\n";}
		}[/COLOR]

```

...thus when you request Celcius, it shows in yer Conky
I would want to make it optional, so I will have to think about it some and get back with some code.

---

### Post by aonegodman on 2008-01-31
> **Bruce M. said:**
> My brand new **Conky 5 Day Forcast (v3.0)** in development.


Now it looks like this attachment.

Cool!  You crazy conkyman you.  :lolflag:

---

### Post by Bruce M. on 2008-01-31
> **aonegodman said:**
> Cool!  You crazy conkyman you.  :lolflag:

[CENTER]**[SIZE="4"]EXCUUUUUSE ME![/SIZE]**[/CENTER]

 =; [COLOR="Red"]**Stop right there!**[/COLOR] =;

*Are you not the one that asked for the*
> Today Tomorrow Sat Sun Mon
*update?*

If I recall correctly it was a 3am thought when you couldn't sleep. :-\"

[CENTER]**[SIZE="4"]You crazy conkyman you.[/SIZE]**
[SIZE="1"]That's my partner there folks![/SIZE][/CENTER]

---

### Post by Cammy on 2008-01-31
Ok, I gots me a problem.  I have too many weather symbols (see below).

Here's my conky:

```
${font proggycleantt:size=10}${alignc}${execi 6000 perl ~/.scripts/weather.pl 20872 f 4d}${font}
${font weather:size=30}${alignc}${execi 6000 perl ~/.scripts/weather.pl 20872 f 4dp}${font}
${voffset -2}${font proggycleantt:size=10}${alignc}${execi 6000 perl ~/.scripts/weather.pl 20872 f 4t}${font}
```

I have the weather.pl that lvleph last posted.

---

### Post by Cammy on 2008-02-01
Weird!!  Ok, nevermind.  Booted up this morning, and it's normal (just need to change some spacing).

Finally got my days of the week!  Woohoo! :D

---

### Post by Crinos512 on 2008-02-01
> **aonegodman said:**
> 
...and then the following three highlited spots in my conkymain -

```

${voffset[COLOR="Blue"] -8[/COLOR]}${color cyan}${font weather:size=[COLOR="Blue"]37[/COLOR]}${alignc}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5dp}$font$color
${color gold}${alignc [COLOR="Blue"]-1[/COLOR]}${execi 14400 perl ~/scripts/lvl-w.pl USTN0132 f 5d}

```

Hope this helps out.    :)

aonegodman what are the lines above the weather fonts, yet below the Weather HR that give you the current conditions?

Specifically I am looking for the Sun rise/set times, moon phase, UV, and Barometric presure.... if they are based on another script could you also post it in it's entirety too?

Thanks! :)

---

### Post by Bruce M. on 2008-02-01
> **Crinos512 said:**
> aonegodman what are the lines above the weather fonts, yet below the Weather HR that give you the current conditions?

Specifically I am looking for the Sun rise/set times, moon phase, UV, and Barometric presure.... if they are based on another script could you also post it in it's entirety too?

Thanks! :)

Let me answer that:
Start by looking at: [7 Easy Steps for 2 Conkys]("http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489") ( weather was the second conky)
[I][LIST]
[*]If you are going to put the conky code in your existing conkyrc file you obviously do not need a second file. Just follow the steps to get the codes you need.
[/LIST][/I]

**To get:**
[LIST=1]
[*]your city code
[*]proper **.sxlt** file for your city
[/LIST]
For the attached image, these are what I am using:

[LIST]
[*]**Conky Code:**
[/LIST]
You will need to change **ARBA0009** to your city code.
```

${color orange}WEATHER: ${color cyan}${hr 1}$color
${color cyan}Lat: ${color orange}34°35'00"S   ${color cyan}Long: ${color orange}58°21'00"W ${alignr} ${color cyan}Alt: ${color orange}25 m$color
${color yellow}${execi 600 ~/scripts/myweather.sh ARBA0009}$color

```

[LIST][*]**myweather.sh file:**[/LIST]

You will need to change:
[LIST=1]
[*]LOCID=ARBA0009 - to your city code
[*]UNITS=m # s=standard units, m=metric units
[/LIST]
```

#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# Modified by Vredfreak
# The orignal script and xslt can be downloaded from http://pondol.com/weather.tar.gz

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use http://xoap.weather.com/search/search?where=[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=ARBA0009

# s=standard units, m=metric units
UNITS=m

# where this script and the XSLT lives
RUNDIR=~/scripts

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at http://curl.haxx.se/
CURLCMD=/usr/bin/curl

# get it at http://xmlsoft.org/XSLT/
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?dayf=10&unit=$UNITS&cc=*"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/myweather.xslt

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"

```

[LIST][*]**myweather.xslt**[/LIST]
```

<!-- 

 This XSLT is used to translate an XML response from the weather.com
 XML API. 

 You can format this file to your liking. Two things you may feel 
 like doing:

	1) Modify the layout of the fields or static text already defined
	2) Add other fields from the XML response file that aren't referenced in this
	   XSLT. You can grab a full list by just doing a: 
           wget "http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS" 
           (change $LOCID and $UNITS to suit your needs)
-->

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" > 
	<xsl:output method="text" disable-output-escaping="yes"/>
	<xsl:template match="weather">
			<xsl:apply-templates select="loc"/>
			<xsl:apply-templates select="cc"/>
			<!-- <xsl:apply-templates select="dayf/day[@d='1']"/> -->
	</xsl:template>
	
			<xsl:template match="loc">

<xsl:text>Live from:  </xsl:text><xsl:value-of select="dnam"/>
<!-- <xsl:text>
Lat: </xsl:text><xsl:value-of select="lat"/>
<xsl:text>                  Long: </xsl:text><xsl:value-of select="lon"/> -->
<xsl:text>
SUN:  Rise: </xsl:text><xsl:value-of select="sunr"/>
<xsl:text>     Set: </xsl:text><xsl:value-of select="suns"/>

			</xsl:template>

			<xsl:template match="cc">
<xsl:text>

Temp: </xsl:text><xsl:value-of select="tmp"/><xsl:value-of select="/weather/head/ut"/>

<xsl:text>              Feels Like: </xsl:text><xsl:value-of select="flik"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text>

Conditions: </xsl:text><xsl:value-of select="t"/>
<xsl:text>
Visibility: </xsl:text><xsl:value-of select="vis"/><xsl:text> KM</xsl:text>
<xsl:text>     Humidity: </xsl:text><xsl:value-of select="hmid"/><xsl:text>%</xsl:text>
<xsl:text>
Wind: </xsl:text>
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>0</xsl:text></xsl:when>
	<xsl:otherwise><xsl:value-of select="wind/s"/></xsl:otherwise>
</xsl:choose>
<xsl:value-of select="/weather/head/us"/> 
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>(0 km/h)</xsl:text></xsl:when>
	<xsl:otherwise><xsl:text> (</xsl:text><xsl:value-of select="round(wind/s * 0.6214)"/><xsl:text> mph)</xsl:text></xsl:otherwise>
</xsl:choose>
<xsl:text> (</xsl:text><xsl:value-of select="wind/t"/>
<xsl:text>)</xsl:text>
<xsl:text>
Gusting to: </xsl:text><xsl:value-of select="wind/gust"/>
<xsl:text> km/h</xsl:text>
<xsl:text>
Barometer: </xsl:text><xsl:value-of select="bar/r"/>
<xsl:text> mb ~ </xsl:text><xsl:value-of select="bar/d"/>

<xsl:text>
UV: </xsl:text><xsl:value-of select="uv/i"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="uv/t"/>
<xsl:text>        Dew Point: </xsl:text><xsl:value-of select="dewp"/><xsl:text> °C</xsl:text>

<xsl:text>

MOON: Day: </xsl:text><xsl:value-of select="moon/icon"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="moon/t"/>

	</xsl:template>

<!--	<xsl:template match="dayf/day[@d='1']">
<xsl:text>

DAY 02: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
 <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
	</xsl:template>

	<xsl:template match="dayf/day[@d='2']">
<xsl:text>
DAY 03: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
 <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
	</xsl:template> -->

</xsl:stylesheet>

```

Hope this helps.
If you have more questions just ask.
Bruce

---

### Post by aonegodman on 2008-02-01
> **Crinos512 said:**
> aonegodman what are the lines above the weather fonts, yet below the Weather HR that give you the current conditions?

Specifically I am looking for the Sun rise/set times, moon phase, UV, and Barometric presure.... if they are based on another script could you also post it in it's entirety too?

Thanks! :)

See Bruce M. new post above. Should answer your question.  :)

---

### Post by aonegodman on 2008-02-01
Ok , using the new weather.pl script posted by lvleph with adding day names I get the following:

< See Attachment please >

All I did to my conkymain script was point it to the new weather.pl. Days show but the the temps under icons disappear.   Where did they go?

Thanks.

---

### Post by Bruce M. on 2008-02-01
> **aonegodman said:**
> Ok , using the new weather.pl script posted by lvleph with adding day names I get the following:

< See Attachment please >

All I did to my conkymain script was point it to the new weather.pl. Days show but the the temps under icons disappear.   Where did they go?

Thanks.

lvleph said things changed in the new script.

You now need three lines for what you want (in what ever order)
[LIST=1]
[*]day names ie: ending with 5d}
[*]weather fonts ie: ending with 5dp}
[*]hi/low temps ie: ending with 5t}
[/LIST]

Like this:

```

${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5d}
${color cyan}${font weather:size=30}${alignc -2}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}$font$color
${color yellow}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5t}$color

```

---

### Post by Cammy on 2008-02-01
I wish there was a way to do this all in a single execi.  I'm up to 4% cpu usage now (up from 2% before adding weather) and I think it's the 3 additional execis.  Wish I could just call one, store the info in a variable or something, then just call that in the conky.

---

### Post by aonegodman on 2008-02-01
> **Bruce M. said:**
> lvleph said things changed in the new script.

You now need three lines for what you want (in what ever order)
[LIST=1]
[*]day names ie: ending with 5d}
[*]weather fonts ie: ending with 5dp}
[*]hi/low temps ie: ending with 5t}
[/LIST]

Like this:

```

${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5d}
${color cyan}${font weather:size=30}${alignc -2}${execi 14400 perl ~/scripts/lvl-w.pl ARBA0009 c 5dp}$font$color
${color yellow}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5t}$color

```

Ok, didn't have my " wheaties " this morning I guess, but . . . .

1) What are you calling "w-days.pl ?"

2) These three go where the bottom "5 Day" weather code below is?

```


${font :size=8}${color cyan}5 Day: ${hr 1}$color

${voffset -8}${color cyan}${font weather:size=37}${alignc}${execi 14400 perl ~/scripts/lvl-w2.pl USTN0132 f 5dp}$font$color
${color gold}${alignc -1}${execi 14400 perl ~/scripts/lvl-w2.pl USTN0132 f 5d}


${font :size=8}${color cyan}GMAIL: ${hr 1}$color
You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new gmail(s).

```

Thanks!  :)

---

### Post by lvleph on 2008-02-02
> **Cammy said:**
> I wish there was a way to do this all in a single execi.  I'm up to 4% cpu usage now (up from 2% before adding weather) and I think it's the 3 additional execis.  Wish I could just call one, store the info in a variable or something, then just call that in the conky.
The issue is the weather fonts. If we didn't have to use weather fonts I could use one execi.

I will see if there is a way to do it in one, but I doubt it.

---

### Post by Bruce M. on 2008-02-02
> **aonegodman said:**
> Ok, didn't have my " wheaties " this morning I guess, but . . . .

1) What are you calling "w-days.pl ?"

One of the 5 **.PL** files I have.  This one shows the day names.
I kept all the old ones as they were upgraded and changed.

> **aonegodman said:**
> 
2) These three go where the bottom "5 Day" weather code below is?

```


${font :size=8}${color cyan}5 Day: ${hr 1}$color

${voffset -8}${color cyan}${font weather:size=37}${alignc}${execi 14400 perl ~/scripts/lvl-w2.pl USTN0132 f 5dp}$font$color
${color gold}${alignc -1}${execi 14400 perl ~/scripts/lvl-w2.pl USTN0132 f 5d}


${font :size=8}${color cyan}GMAIL: ${hr 1}$color
You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new gmail(s).

```

Thanks!  :)

This is what you need (along with the latest **.PL** file if you do not have it:

```

${font :size=8}${color cyan}5 Day: ${hr 1}$color

${execi 14400 perl ~/scripts/lvl-w2.pl USTN0132 f 5d}
${voffset -8}${color cyan}${font weather:size=37}${alignc -2}${execi 14400 perl ~/scripts/lvl-w2.pl USTN0132 f 5dp}$font$color
${color gold}${execi 14400 perl ~/scripts/lvl-w2.pl USTN0132 f 5t}$color

${font :size=8}${color cyan}GMAIL: ${hr 1}$color
You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new gmail(s).

```

Check your **lvl-w2.pl** file if the first 15 lines look like this, you [COLOR="Red"]**NEED**[/COLOR] the newest **.PL** file:

```

#!/usr/bin/perl

use Switch;
use Encode;

# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

$spaces="  "; #spacing between each high low.
$fspaces=" "; #spacing between condition symbols.

```

In the latest **.PL** file the first 15 lines look like this: (Get the complete file if you do not have it).

```

#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

```

There you go partner!
Bruce

---

### Post by Cammy on 2008-02-02
I need to learn perl so I can get this thing to do what I want with fewer execis.  2% CPU usage just for the weather is a bit much.

Has anyone else noticed an increase in CPU usage like this?

---

### Post by lvleph on 2008-02-02
Wht do you want it to do?
There is no way to display the condition symbols without its own executable. Everything else can be done with one run. You just have to tell me what you want.

EDIT: The amount of CPU usage and even MEM usage should still be pretty low, since the default setup is to run once an hour for each input type. Also, the number of operations that the script goes through is relatively low. If you are experience high CPU usage from conky it is probably something else.

---

### Post by tad1073 on 2008-02-02
Is it possible to use images instead of fonts for the sun and clouds and what not?

---

### Post by lvleph on 2008-02-02
As far as I know, no.

---

### Post by tad1073 on 2008-02-02
Just wondering. I found some nice weather images on [deviant art](http://jyrik.deviantart.com/art/Weather-Icons-Shiny-5215175?offset=10#comments)

---

### Post by Bruce M. on 2008-02-02
> **lvleph said:**
> Wht do you want it to do?
There is no way to display the condition symbols without its own executable. Everything else can be done with one run. You just have to tell me what you want.

Are you saying you can combine these two lines into one **execi** call:

```

${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5d}
${color yellow}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5t}$color

```

so that they show:
```

 Noche   Mañana     Lun     Mar     Mié
27°/16°  26°/17°  28°/16° 30°/17° 30°/20°

```
And maintain the ability to **space them seperately** as we can today? [-o<

Then I'd just pop the weather symbols above that.

You'd be my hero!
Bruce

BTW. My latest conky:
[CENTER]
[[IMG]http://img215.imageshack.us/img215/9721/screenshotqw1.th.png[/IMG]](http://img215.imageshack.us/my.php?image=screenshotqw1.png)
[/CENTER]

---

### Post by lvleph on 2008-02-02
Yes, I can do that. Give me about 10-20 mins.

---

### Post by Bruce M. on 2008-02-02
> **lvleph said:**
> Yes, I can do that. Give me about 10-20 mins.

Naw!  You're joking right!

**[COLOR="Blue"]Wait until Cammy & aonegodman see this.  :)[/COLOR]**

---

### Post by sunzaru on 2008-02-02
nice.  Conky helps remove me from the TV.  No need to watch weather channel in morning ;)

i'm in windows atm.. playing wow because i still havn't gotten wine to work right w/ it.  but i'll look @ conky later.  nice post.

---

### Post by Bruce M. on 2008-02-02
> **sunzaru said:**
> nice.  Conky helps remove me from the TV.  No need to watch weather channel in morning ;)

i'm in windows atm.. playing wow because i still havn't gotten wine to work right w/ it.  but i'll look @ conky later.  nice post.

Yea, **lvleph** is a genius!

---

### Post by lvleph on 2008-02-02
Okay, I made it so the out has the temps and then the days.

Just use the option 5td. This will give you 5 days of temps and day names.

```
#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update }le if set to 0 don't use }le

$spaces="     "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="    ";
$Text::Wrap::columns = 55;

$initial_tab=""; #tab before first line in weather output
$subsequent_tab="\t"; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Feels like:  $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #how many days are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		my $count=0;
		my $day=(split "t", $what)[0]; #how many days are we looking for
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]td$/ {
		&file_op; #save weather to $file
		my $count1 = my $count2=0;
		my $day=(split "dt", $what)[0]; #how many days are we looking for
		my $flag=1; #print days once
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if(/<th>(\b.+\b)<\/th>/ && ++$count1<=$day){ #look for the conditions upto specified day
				$days[$count1-1]=$1; #save day
				&day_space($days);
			}
			elsif($high=~/\d+/ && $low=~/\d+/ && ++$count2<=$day){$ttext.=$high.$degree."/".$low.$degree.$spaces;}
			elsif($count1>=$day && $count2>=$day){print "$ttext\n$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-5]td displays high/low temp in chosen system and then days up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size >= 1000){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	$ctext.=$_.$fspaces;
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Today ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```

---

### Post by lvleph on 2008-02-02
I already found one issue with it. Damn conky cannot offset more than the first line of text.

I am going to have to think about this.

---

### Post by Bruce M. on 2008-02-02
> **lvleph said:**
> I already found one issue with it. Damn conky cannot offset more than the first line of text.

I am going to have to think about this.

They line up perfectly!

Only one thing - one colour.  A price to pay.  :)

EDIT:  See you tomorrow.

Thanks a lot.
Bruce

---

### Post by lvleph on 2008-02-02
My weather is centered in the conky window so it doesn't line up properly for me. I could add a space variable, but I don't really want to do that. What I would like is for conky to handle offsets correctly.

---

### Post by Cammy on 2008-02-03
> **lvleph said:**
> Wht do you want it to do?
EDIT: The amount of CPU usage and even MEM usage should still be pretty low, since the default setup is to run once an hour for each input type. Also, the number of operations that the script goes through is relatively low. If you are experience high CPU usage from conky it is probably something else.

It's the weather alright.  Pulling only the weather out puts me at 2% on idle.  Adding the 3 execis for the weather and restarting conky puts me back at 4%.

But your fix worked.  I'm now at 3% with just the two lines.  It's not as pretty (I used to have the days first, then symbols, then temps) but I understand that it has to be the way it is.

Thanks for the change.  1% increase in CPU usage I can live with.

---

### Post by Cammy on 2008-02-03
> **Cammy said:**
> It's not as pretty (I used to have the days first, then symbols, then temps) but I understand that it has to be the way it is.

I stand corrected!  I just got it to do this with two execis:

day
symbol
temps

:D

I wonder if Bruce can figure out how. ;)

---

### Post by lvleph on 2008-02-03
Can you post the solution to that. I think I know how you did it, but it is not very useful to others to just post the image. (I am guessing grep and awk). I could make it so that one can choose the number of endlines between the days and the temps and then the user places the weather icons using voffset.

---

### Post by Cammy on 2008-02-03
> **lvleph said:**
> Can you post the solution to that. I think I know how you did it, but it is not very useful to others to just post the image. (I am guessing grep and awk). I could make it so that one can choose the number of endlines between the days and the temps and then the user places the weather icons using voffset.

Yeah, sorry, I just wanted to tease Bruce. ;)

The solution isn't nearly as cool as you guessed though.

First I edited weather.pl to get the day on top and the temps on the bottom.

Then I added some line breaks (\n) between them.

I put the line for the symbols first in conkyrc, then put a huge voffset on the line with the days/temps so that it moved them up so the symbols were in the space caused by the line breaks.

Modification to weather.pl (line 136 in mine):

[PHP]elsif($count1>=$day && $count2>=$day){print "$dtext\n\n\n\n$ttext\n"; exit;} #don't keep lopking if everything has been found[/PHP]

conkyrc:
[PHP]
<space here>
${font weather:size=30}${alignc}${execi 6000 perl ~/.scripts/weather.pl 20872 f 4dp}${font}
${voffset -47}${font proggycleantt:size=10}${alignc}${execi 6000 perl ~/.scripts/weather.pl 20872 f 4td}${font}[/PHP]

Of course, don't keep the <space here>.  Just make it a space, otherwise the days will be on top of anything you have on the line above.  Change the number of \n's and the voffset to suit the size/font/etc of your conky.

---

### Post by lvleph on 2008-02-03
lol, I didn't think you would change the script.

I just implemented that solution (kind of funny that we both did the same thing) and then renamed the option for both the temp and days together to be 5dt instead of 5td.

To change the number of lines between the temps and the days use the variable $lines on line 20.

```
#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update $file if set to 0 don't use $file

$spaces="     "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="    ";
$lines="\n\n\n\n"; #each \n represents one line between the days and temps

$Text::Wrap::columns = 55;
$initial_tab=""; #tab before first line in weather output
$subsequent_tab="\t"; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Feels like:  $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #how many days are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		my $count=0;
		my $day=(split "t", $what)[0]; #how many days are we looking for
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]dt$/ {
		&file_op; #save weather to $file
		my $count1 = my $count2=0;
		my $day=(split "dt", $what)[0]; #how many days are we looking for
		my $flag=1; #print days once
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if(/<th>(\b.+\b)<\/th>/ && ++$count1<=$day){ #look for the conditions upto specified day
				$days[$count1-1]=$1; #save day
				&day_space($days);
			}
			elsif($high=~/\d+/ && $low=~/\d+/ && ++$count2<=$day){$ttext.=$high.$degree."/".$low.$degree.$spaces;}
			elsif($count1>=$day && $count2>=$day){print "$dtext\n$lines$ttext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-5]dt displays high/low temp in chosen system and then days up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size >= 1000){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	$ctext.=$_.$fspaces;
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Today ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```

---

### Post by Cammy on 2008-02-03
Hey that's cool!  I think there's a missng } or something though, because when I use that script I get a screenful of xml code.

---

### Post by Bruce M. on 2008-02-03
> **Cammy said:**
> It's the weather alright.  Pulling only the weather out puts me at 2% on idle.  Adding the 3 execis for the weather and restarting conky puts me back at 4%.

But your fix worked.  I'm now at 3% with just the two lines.  It's not as pretty (I used to have the days first, then symbols, then temps) but I understand that it has to be the way it is.

Thanks for the change.  1% increase in CPU usage I can live with.

Got you beat!  Sitting idle my CPU usage was at 27%.  Found out it was because I was calling it every second to have the seconds in the big clock. Changed conky, dropping seconds and calling every 8 seconds. Idle time usage dropped to 4%, with weather running 4 execi calls.
[LIST=1]
[*]Is the regular weather call with the **.XSLT** and **.SH** files to get todays conditions.
[*] With lvleph's **.PL** file for **weather fonts**
[*] With lvleph's **.PL** file for **day names**
[*] With lvleph's **.PL** file for **hi/lows**
[/LIST]

Now I'm down to 3 execi calls and floating between 2-3% idle usage, I can live with that.  :)

---

### Post by Bruce M. on 2008-02-03
> **lvleph said:**
> My weather is centered in the conky window so it doesn't line up properly for me. I could add a space variable, but I don't really want to do that. What I would like is for conky to handle offsets correctly.

So is mine, it's centered in my conkymain file  :)

> **Cammy said:**
> I stand corrected!  I just got it to do this with two execis:

day
symbol
temps

:D

I wonder if Bruce can figure out how. ;)
Arriving late, I got to read it all in one sweep. :-\"
> **Cammy said:**
> Yeah, sorry, I just wanted to tease Bruce. ;)
You're BAD, and that's GOOD! 
I, not being a programmer, would never have found out.
But I see from the next quote, I don't have too.  :tongue:

> **lvleph said:**
> lol, I didn't think you would change the script.

I just implemented that solution (kind of funny that we both did the same thing) and then renamed the option for both the temp and days together to be 5dt instead of 5td.

To change the number of lines between the temps and the days use the variable $lines on line 20.

```
#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update $file if set to 0 don't use $file

$spaces="     "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="    ";
$lines="\n\n\n\n"; #each \n represents one line between the days and temps

$Text::Wrap::columns = 55;
$initial_tab=""; #tab before first line in weather output
$subsequent_tab="\t"; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Feels like:  $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #how many days are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		my $count=0;
		my $day=(split "t", $what)[0]; #how many days are we looking for
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]dt$/ {
		&file_op; #save weather to $file
		my $count1 = my $count2=0;
		my $day=(split "dt", $what)[0]; #how many days are we looking for
		my $flag=1; #print days once
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if(/<th>(\b.+\b)<\/th>/ && ++$count1<=$day){ #look for the conditions upto specified day
				$days[$count1-1]=$1; #save day
				&day_space($days);
			}
			elsif($high=~/\d+/ && $low=~/\d+/ && ++$count2<=$day){$ttext.=$high.$degree."/".$low.$degree.$spaces;}
			elsif($count1>=$day && $count2>=$day){print "$dtext\n$lines$ttext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-5]dt displays high/low temp in chosen system and then days up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size >= 1000){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	$ctext.=$_.$fspaces;
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Today ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```

Grabbed it .... going to play ... be right back!

---

### Post by Bruce M. on 2008-02-03
> **Cammy said:**
> Hey that's cool!  I think there's a missng } or something though, because when I use that script I get a screenful of xml code.

Yea, me too.  :(

Did you find it?

**EDIT:** Line # { }
[LIST]
[*]040 -  open 7 - close 6
[*]059 - open 13 - close 12
[*]069 - open 17 - close 16
[*]079 - open 21 - close 20
[*]091 - open 25 - close 24
[*]106 - open 30 - close 29
[*]120 - open 34 - close 33
[*]139 - open 39 - close 38
[*]157 - open 43 - close 42
[*]171 - open 48 - close 47
[*]182 - open 51 - close 50
[*]201 - open 52 - close 52 <<-- even
[*]229 - open 58 - close 58
[*]240 - open 66 - close 66
[*]254 - open 77 - close 77
[/LIST]
Don't think that's the problem.

---

### Post by Cammy on 2008-02-03
> **Bruce M. said:**
> Yea, me too.  :(

Did you find it?

No, I just added the $lines thingy to my current one.

---

### Post by lvleph on 2008-02-03
Mine seems to work fine, so here it is again.

```
#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update $file if set to 0 don't use $file

$spaces="     "; #spacing between each high low.
$fspaces=""; #spacing between condition symbols.
$dspaces="    ";
$lines="\n\n\n\n"; #each \n represents one line between the days and temps

$Text::Wrap::columns = 55;
$initial_tab=""; #tab before first line in weather output
$subsequent_tab="\t"; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Feels like:  $tmf$degree\n";
					print "Humidity:    $hmt%\n"; 
					print "Wind:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #how many days are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		my $count=0;
		my $day=(split "t", $what)[0]; #how many days are we looking for
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]dt$/ {
		&file_op; #save weather to $file
		my $count1 = my $count2=0;
		my $day=(split "dt", $what)[0]; #how many days are we looking for
		my $flag=1; #print days once
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if(/<th>(\b.+\b)<\/th>/ && ++$count1<=$day){ #look for the conditions upto specified day
				$days[$count1-1]=$1; #save day
				&day_space($days);
			}
			elsif($high=~/\d+/ && $low=~/\d+/ && ++$count2<=$day){$ttext.=$high.$degree."/".$low.$degree.$spaces;}
			elsif($count1>=$day && $count2>=$day){print "$dtext\n$lines$ttext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		&usage; #print usage error
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size >= 1000){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub usage { #if correct options haven't been passed usage error
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-5]dt displays high/low temp in chosen system and then days up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	$ctext.=$_.$fspaces;
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Today ";}
	elsif ($_ =~ "Tonight"){$_="Tonight";}
	elsif ($_ =~ "Tomorrow"){$_="Tomorrow";}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```

---

### Post by martynp on 2008-02-03
Guys,

Have got the original post working nicely after some format changes. Many thanks for this.

Have been following this thread and was wondering if you could do another how-to now the scripts have advanced significantly.

I have tried the above but is was a bit messy so reverted back.

Would love a script and a how-to like at the start of the thread to achieve the changes you have made. Also to get the full forecast on conky like some guy posted in another thread.

Many Thanks

---

### Post by lvleph on 2008-02-03
> **martynp said:**
> Guys,

Have got the original post working nicely after some format changes. Many thanks for this.

Have been following this thread and was wondering if you could do another how-to now the scripts have advanced significantly.

I have tried the above but is was a bit messy so reverted back.

Would love a script and a how-to like at the start of the thread to achieve the changes you have made. Also to get the full forecast on conky like some guy posted in another thread.

Many Thanks

It is still beta in its current form. When it is complete, I will post everything in the original post.

---

### Post by martynp on 2008-02-03
Hi,

Thanks for the reply.

Understood.... waiting with anticipation.

Great work and thanks again.

---

### Post by lvleph on 2008-02-03
Updated to newest version. Including addition by LazarusHC, plus many more.

---

### Post by martynp on 2008-02-04
Hi,

Everything working nicely with some formatting tweaks.... great job.

Just one thing:

Your Line: ${execi 3600 perl ~/scripts/weather.pl USVA0652 f 7w}
My Line: (${execi 1800 perl ~/Conky/weather.pl UKXX0212 c 7w}

returns the text forecast in Farenheit and not Centigrade (imperial not metric)

All other calls return metric when requested.

Any ideas?

---

### Post by Bruce M. on 2008-02-04
> **lvleph said:**
> It is still beta in its current form. When it is complete, I will post everything in the original post.

Grabbed the latest .. works great!

---

### Post by lvleph on 2008-02-04
Apparently the text weather from the website that I get it from only comes in imperial. I may work out a solution for that though.

---

### Post by aonegodman on 2008-02-04
> **Cammy said:**
> I need to learn perl so I can get this thing to do what I want with fewer execis.  2% CPU usage just for the weather is a bit much.

Has anyone else noticed an increase in CPU usage like this?

I notice an average 10 to 12% CPU usage from conky myself. The Gmail call kicks it up about 18% on fetch.

I am not using the new weather with days set up yet as on second thought I don't think I really need it for the third execi call. 

Hey, if I know what day **today** is, then I still gots enough beans to figure the rest out for myself.

:lolflag:

---

### Post by lvleph on 2008-02-04
You can do the days and temps in one call, using the [1-5]dt option.

Oh and it is a good thing that I am using perl instead of python, because then it would use more cpu. However, I do believe it is conky using up the cpu not the weather script. If you were to run weather in command line and watch the cpu usage you would see what I mean.

---

### Post by Cammy on 2008-02-04
> **lvleph said:**
> However, I do believe it is conky using up the cpu not the weather script. If you were to run weather in command line and watch the cpu usage you would see what I mean.

What's probably causing my cpu usage increase is probably not the weather script or conky now that I think about it.  It's probably the symbols font.

A few weeks ago I tried to dress up my conky by adding symbols using the StyleBats font.  When I got done, I noticed that conky was using something screwy like 50% cpu.  Pulling only the StyleBats font calls out dropped it back to 2% overall cpu use, so I went back to just having text.

I have no idea why fonts get my conky in an uproar.

---

### Post by Bruce M. on 2008-02-04
> **Cammy said:**
> A few weeks ago I tried to dress up my conky by adding symbols using the StyleBats font.  When I got done, I noticed that conky was using something screwy like 50% cpu.  Pulling only the StyleBats font calls out dropped it back to 2% overall cpu use, so I went back to just having text.

I have no idea why fonts get my conky in an uproar.

In the: [ Post your .conkyrc files w/ screenshots]("http://ubuntuforums.org/showthread.php?t=281865") thread they talked about that a lot.  The StyleBats font do chew up CPU usage, so a lot of people dropped them for that reason.

---

### Post by craigeo on 2008-02-06
I have this working in my .conkyrc except I can't get the symbol weather fonts to display.
They come up as e cKKKK
Also, the F (farenheit) symbol displays as an A with symbol on top of it.
So, it looks like I'm doing something wrong with the weather font, but can't figure out what it is.
Anyone have any ideas?

---

### Post by lvleph on 2008-02-06
Did you read all of the directions including the notes?
The symbols require the weather font, which means you have to install them and then you have to use use the font variable in conky to get them to display correctly. The A in place of the degree symbol is because you have to have use_xft yes and it could be the font you are using. All of this is covered in the directions. If you post your conkyrc I could be of more help.

---

### Post by craigeo on 2008-02-06
I'm at work now so will have to look when I get home.
I went through all the directions twice, so I must be doing the same mistake twice.

---

### Post by bardic on 2008-02-06
Sorry if this is a stupid question but how do I find my city code?

---

### Post by lvleph on 2008-02-06
Delete

---

### Post by lvleph on 2008-02-06
Find your city code. You can go to weather.com and put in your city in the search. It will then ask you to select the city that you meant. Select that, once the page has loaded look at the address bar for a number after the last / (it should include letters too).

---

### Post by bardic on 2008-02-06
Hey, I got my city code and almost everything working. The only problem is now there are only two tempatures appearing....

Here is the code...
```

${color ffffff}Weather ${hr 2}$color
${voffset -5}${font weather:size=30}${alignc}${offset -45}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 1p}${offset 25}${color ffffff}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 2p}${offset 25}${color ffffff}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 3p}${offset 24}${color ffffff}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 4p}${offset 23}${color ffffff}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 5p}${font}$color
${alignc}${offset -15}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 1}${offset 10}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 2}${offset 35}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 3}${offset 60}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 4}${offset 85}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 5}

```

I've tried all the code in this thread an i'm only getting two temps...

---

### Post by lvleph on 2008-02-06
Well, it could be your offset. I am unsure. Trying running 
```
~/scripts/weather.pl CAXX0183 c 1
```
in the terminal for each day you want displayed. If you get a temp for everyday, then it would have to be the offset.
Also, it would be easier to just use 
```
${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 5t}
``` in conky and play with the spacing using the $spaces variable.

---

### Post by bardic on 2008-02-06
played with the spaces and replaced the old line with this 

```
${alignc}${offset 5}${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 5t} 
```

and it works beautifully! thanks a lot mate.

---

### Post by lvleph on 2008-02-06
If you don't care about having different colored weather icons you can also use
```
${execi 3600 perl ~/scripts/weather.pl CAXX0183 c 5p}
```

---

### Post by bardic on 2008-02-06
[Here]("http://farm3.static.flickr.com/2152/2247736686_4dc52d3482_o.png") is my setup. I'm gonna keep playing to see what I can do with it ^^

---

### Post by lvleph on 2008-02-06
I don't believe I have ever posted my complete conky, so here it is.

---

### Post by craigeo on 2008-02-06
I'm using the exact conkyrc from the first page and the weather icons still don't show.  The degrees shows fine now, but the weather font still shows as AkkkC

---

### Post by lvleph on 2008-02-06
Did you download the weather font and install it?

---

### Post by craigeo on 2008-02-07
Yup I did. But thanks for your help.
I finally just wiped all of it out, and started completely over and now it's working fine and I've integrated it with the rest of my settings.
Now working on tweaking it.
No idea what I was doing wrong, but obviously either missed something or fat fingered something.
Thanks again for your help.

---

### Post by SanskritFritz on 2008-02-07
> **lvleph said:**
> I don't believe I have ever posted my complete conky, so here it is.Care to post the .conkyrc contents? Thanks!

---

### Post by aonegodman on 2008-02-07
> **SanskritFritz said:**
> Care to post the .conkyrc contents? Thanks!

DITTO please.   :)

---

### Post by lvleph on 2008-02-07
I have an if statement in it so that if I am not connected with wireless it shows my wired stats. Just incase someone gets confused about that.

```
# UBUNTU-CONKY.

# Update interval in seconds
update_interval 1.0

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
xftfont Candera:size=6
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
color0 97b9f4
color1 orange
color2 red
color3 green

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${alignc}${offset -20}${color0}${font Arial:bold:size=12}${time %H:%M:%S}$font
${alignc}${time %A}, ${time %d %B %G}$color
${color1}$hr
${voffset -3}$alignc GMAIL
${voffset -7}$hr $color
You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new email(s).
${execi 60 perl ~/scripts/gmail.pl s}
${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS 
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl USVA0652 f w}
${voffset -30}$alignr${offset -50}$color1${execi 3600 perl ~/scripts/weather.pl USVA0652 f t}$color
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USVA0652 f cp}$font
${voffset -15}${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST 
${voffset -7}$hr $color
${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5dp}${font}$color
$color1${voffset -55}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5dt}$color
${execi 3600 perl ~/scripts/weather.pl USVA0652 f 7w}
${color1}$hr
${voffset -3}$alignc SYSTEM
${voffset -7}$hr $color
${exec cat /etc/issue.net}
$sysname Kernel $kernel ($machine)
Uptime: $uptime
Battery status: $acpiacadapter, $battery 
${color1}$hr
${voffset -3}$alignc CPU/MEM
${voffset -7}$hr $color
${cpugraph 40,250 000000 ff0000}
${voffset -45}${execi 10 head /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //' | cut -b 0-20,31-48}
Clock: ${freq}MHz${alignr}Usage: ${cpu}%        Temp: ${acpitemp}C
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color
${color1}$hr
${voffset -3}$alignc FILE SYSTEM
${voffset -7}$hr $color
Root:  ${fs_free}/${fs_size /} ${fs_bar 6 /}
Home:  ${fs_free /home}/${fs_size /home} ${fs_bar 6 /home}
${if_mounted /media/samba/}Samba:  ${fs_free /media/samba}/${fs_size /media/samba} ${fs_bar 6 /media/samba}
${color1}$hr 
${else}${color1}$hr $endif
${voffset -3}$alignc NETWORK
${voffset -7}$hr $color
${if_empty ${exec python ~/scripts/wifiUp.py}} ${downspeedgraph eth0 35,124 000000 ff0000 1126} ${upspeedgraph eth0 35,124 000000 00ff00 300}$color
${voffset -40}${alignc}WIRED
Local IP: ${addr eth0} $alignr Public IP: ${execi 18000 ~/scripts/myip.sh}
Down: ${downspeed eth0} kb/s $alignr Up: ${upspeed eth0} kb/s
Total: ${totaldown eth0} $alignr Total: ${totalup eth0}
${else}${downspeedgraph wlan0 44,124 000000 ff0000 1126} ${upspeedgraph wlan0 44,124 000000 00ff00 300}$color
${voffset -55}${alignc}ESSID:"${wireless_essid wlan0}"
Local IP: ${addr wlan0} $alignr Public IP: ${execi 18000 ~/scripts/myip.sh}
Signal: ${exec ~/scripts/wifiQ.sh}% $alignr Bit Rate: ${exec ~/scripts/wifiBR.sh} Mb/s
Down: ${downspeed wlan0} kb/s $alignr Up: ${upspeed wlan0} kb/s
Total: ${totaldown wlan0} $alignr Total: ${totalup wlan0}$endif
```

---

### Post by Cammy on 2008-02-08
This defies rational explanation...

After "finishing" my conky setup, I realized that I didn't have anything that showed what the temp is *now*.  With no room to add anything else, I made the decision to split my weather conky out and stick it on the opposite side of the screen.  Then I remembered the whole CPU usage thing, since I would need another execi to show current conditions.

After thinking about it, I decided to give it a try anyway.  To my surprise, even with the extra execi, my CPU usage actually went *down* a bit.  Instead of a steady 3%, it now bounces between 2% and 3%, spending more time on 2 than on 3.

I'm now wondering if CPU usage increases with conky as the .conkyrc file size grows, regardless of what it contains.   I can't think of anything else that makes sense.

---

### Post by bardic on 2008-02-08
I have a descent size coknyrc file and my cpu usage is between 0.8% and 1.33%.

---

### Post by Cammy on 2008-02-08
> **bardic said:**
> I have a descent size coknyrc file and my cpu usage is between 0.8% and 1.33%.

Maybe it's something with my machine then.

With a full conky (including displays for processor type, speed, video card type, video mem, vid temp, etc) I was at 2% usage.  Adding weather with 3 execis brough me up to 4%, but now having weather (and still with 3 execis) in a separate conky, I'm back down to 2%.

Told you it defies explanation!

Maybe conky hates to have too many different fonts defined?

---

### Post by lvleph on 2008-02-10
I am surprised there haven't been any replies to this thread in two days. I keep feeling like I should be doing something with weather. lol

---

### Post by Cammy on 2008-02-10
> **lvleph said:**
> I am surprised there haven't been any replies to this thread in two days. I keep feeling like I should be doing something with weather. lol

Can't mess with perfection!

---

### Post by lvleph on 2008-02-10
I am sure there is something that can make it better, but I have not really figure out how to yet. I know bruce wants 10day, but with the current set up I don't think I want to takle that.

---

### Post by noremac on 2008-02-10
Is it possible to change the font size of just the text based information in conky? 

I really like the text info, but it goes beyond the bottom of my monitor with the last day it is supposed to display. I am just getting toooo much in this conky, but cant seem to get rid of any of it. Too useful,

Thanks for any help,
-Cameron

---

### Post by Cammy on 2008-02-11
> **noremac said:**
> Is it possible to change the font size of just the text based information in conky?

${font Myfont:size=##} where Myfont is the name of the font you want to use, and ## is the size.

Example: ${font Versa:size=12}Text here${font}


> **noremac said:**
> I am just getting toooo much in this conky, but cant seem to get rid of any of it. Too useful,

I had the same problem, that's why I pulled the weather out and put it elsewhere on my screen by running two separate conkys.

---

### Post by lvleph on 2008-02-11
And then you will probably need to change where the text wraps. Using the variable $Text::Wrap::columns in the weather script. I believe that is near line 17. The number represents the number of columns before wrapping to the next line. After changing to a smaller font you will want to make that number larger.

---

### Post by Nythain on 2008-02-11
ok, i know you covered the variables in the first post... but it would be nice to include a little more info and possibly some examples of changes...
Like:
If i increase my weather font, should increase or decrese the spacing, and wich spacing, leading or trailing
If i increase the regular font that displays the temp and current weather info, once again with the spacing
Then there's those lines... is that like how much verticle space will be between the day and the temp? I know that some of this has been touched on in other posts here, but centralizing it with some possible examples couldnt hurt... it took me like 3 hours of tweaking font sizes, spacing and everything before i finally got a weather output that looked remotely decent (its still pretty off, but i can deal) and i only finally got it because i read through like EVERY post in the thread till the spacing suggestions were mentioned with rough examples

Just a thought :) Other than that, great freaking work man...
On a side note... does anyone know for near sure wether or not runnign multiple conkys to do things instead of one big one will either cut back cpu usage or increase it or not affect it all???

---

### Post by noremac on 2008-02-11
Thanks for the help. I am realllly liking conky now. So much information and I am not displaying everything I'd like still. Looks so nice! Thanks!

-Cameron

---

### Post by Cammy on 2008-02-11
> **lvleph said:**
> I am sure there is something that can make it better, but I have not really figure out how to yet. I know bruce wants 10day, but with the current set up I don't think I want to takle that.

TEN days!?!?   Must be nice to live in an are where you can actually predict 10 days in advance.  Where I live, once you go past three days ahead, the margin of error becomes so great that you might as well use a magic 8-ball.

One week forecasts don't do much better than 50/50 here, so you honestly might as well guess.

---

### Post by aonegodman on 2008-02-11
> **lvleph said:**
> I am sure there is something that can make it better, but I have not really figure out how to yet. I know bruce wants 10day, but with the current set up I don't think I want to takle that.

Bruce just wants something to fiddle with.  :lolflag:

I'm pretty content with my conky right now. Hanging in there with the 5 Day Plan.  :)

I'm trying to get my Logitech USB Headset working now, that's my current project. Haven't found a solution yet on the forums but still looking.  Please ignore my off subject babbling . . . see ya!

---

### Post by Cammy on 2008-02-11
Here's my final weather conky, nestled in the bottom left corner of my screen.

---

### Post by lvleph on 2008-02-11
> **Nythain said:**
> ok, i know you covered the variables in the first post... but it would be nice to include a little more info and possibly some examples of changes...
Like:
If i increase my weather font, should increase or decrese the spacing, and wich spacing, leading or trailing
If i increase the regular font that displays the temp and current weather info, once again with the spacing
Then there's those lines... is that like how much verticle space will be between the day and the temp? I know that some of this has been touched on in other posts here, but centralizing it with some possible examples couldnt hurt... it took me like 3 hours of tweaking font sizes, spacing and everything before i finally got a weather output that looked remotely decent (its still pretty off, but i can deal) and i only finally got it because i read through like EVERY post in the thread till the spacing suggestions were mentioned with rough examples

Just a thought :) Other than that, great freaking work man...
On a side note... does anyone know for near sure wether or not runnign multiple conkys to do things instead of one big one will either cut back cpu usage or increase it or not affect it all???

Well, if someone were to rewrite the directions, I would post it, but right now I don't have the time. I am a PhD student so...

---

### Post by aonegodman on 2008-02-12
> **Cammy said:**
> Here's my final weather conky, nestled in the bottom left corner of my screen.

Looks good Cammy.   :)

---

### Post by Nythain on 2008-02-12
> **Cammy said:**
> Here's my final weather conky, nestled in the bottom left corner of my screen.
so thats about absolutely perfect, any way you can post the relevant section of your conkyrc???

---

### Post by Cammy on 2008-02-12
> **Nythain said:**
> so thats about absolutely perfect, any way you can post the relevant section of your conkyrc???

Sure can.  I'll post it as soon as I get home (and after I vote!)

---

### Post by lvleph on 2008-02-12
Updated code to include Fog as Cloudy. I really need to find a better weather font.

---

### Post by Cammy on 2008-02-12
> **Nythain said:**
> so thats about absolutely perfect, any way you can post the relevant section of your conkyrc???

```
TEXT
${offset 165}${font weather:size=48}${execi 900 perl ~/.scripts/weather.pl USMD000 f 1dp}${font}
${voffset -50}${color slate grey}Currently:${color}   ${execi 900 perl ~/.scripts/weather.pl USMD000 f t}
${execi 900 perl ~/.scripts/weather.pl USMD000 f w}
${color slate grey}${hr 1}${color}

${font weather:size=35}${execi 3600 perl ~/.scripts/weather.pl USMD000 f 4dp}${font}
${voffset -56}${execi 3600 perl ~/.scripts/weather.pl USMD000 f 4td}
```

Edit to suit

---

### Post by Nythain on 2008-02-12
sweet... well here's what i came up with:
```

# Use Xft?
use_xft yes

# Xft font when Xft is enabled
xftfont Century Schoolbook L:pixelsize=12

# Text alpha when using Xft
xftalpha 1.0

# Minimum size of text area
minimum_size 420 125
maximum_width 420

# Gap between borders of screen and text
# same thing as passing -x at command line
gap_x 1175
gap_y 25

# Force UTF8? note that UTF8 support required XFT
override_utf8_locale yes

TEXT
${font Century Schoolbook L:size=14}Kansas City Weather$hr${font} 
Currently: ${execi 1800 perl ~/.scripts/weather.pl USMO0460 f t}
${execi 1800 perl ~/.scripts/weather.pl USMO0460 f w}
${font Century Schoolbook L:size=14}Five Day Forecast$hr$font

${font weather:size=46}${execi 1800 perl ~/.scripts/weather.pl USMO0460 f 5dp}$font
${voffset -75}${execi 1800 perl ~/.scripts/weather.pl USMO0460 f 5dt}$color

```
and it looks like this (in the upper right corner obviously):

---

### Post by SanskritFritz on 2008-02-13
> **lvleph said:**
> Updated code to include Fog as Cloudy. I really need to find a better weather font.[http://www.dafont.com/search.php?psize=m&q=weather](http://www.dafont.com/search.php?psize=m&q=weather)
[http://www.1001fonts.com/search.html?query=weather](http://www.1001fonts.com/search.html?query=weather)

---

### Post by lvleph on 2008-02-13
> **SanskritFritz said:**
> [http://www.dafont.com/search.php?psize=m&q=weather](http://www.dafont.com/search.php?psize=m&q=weather)
[http://www.1001fonts.com/search.html?query=weather](http://www.1001fonts.com/search.html?query=weather)

None of those have what I am looking for. Maybe, I will look into how to make a font and base it off the weather.com images. When I have time, of course.

---

### Post by Cammy on 2008-02-13
> **Nythain said:**
> and it looks like this (in the upper right corner obviously):

looks good mang! :)

---

### Post by maxehhh on 2008-02-15
any idea why the font in the 5 day forecast is not right?

[img]http://img136.imageshack.us/img136/6664/weatherxp5.jpg[/img]

---

### Post by lvleph on 2008-02-15
Just make it larger, by changing the ${font weather:size=45} in your conkyrc

It looks like you may need to play around with your alignment after that.

---

### Post by gazj on 2008-02-15
For some reason I can't get this to work with UK, the right page downloads in /tmp, but I always get the same (wrong) output.

A couple of examples

```
[gary@Lister tmp]$ weather UKXX0110 c t
68°
[gary@Lister tmp]$ weather UKXX0085 c t
68°

```

The top one is Peterborough UK
and the bottom is London UK

---

### Post by gazj on 2008-02-15
Sorry my fault I saved it with the .pl which was causing problems. :) Thanks

---

### Post by maxehhh on 2008-02-15
> **lvleph said:**
> Just make it larger, by changing the ${font weather:size=45} in your conkyrc

It looks like you may need to play around with your alignment after that.

i changed the size and tried alignr and alignc but still there's not enough space between each one.

---

### Post by Bruce M. on 2008-02-15
> **maxehhh said:**
> i changed the size and tried alignr and alignc but still there's not enough space between each one.

I have a screen resolution of: 1280 x 1024.  If you have that you can try mine:

**Conky file:**
```

${color cyan}${hr 1} $color
${color gold}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5d}
${color cyan}${font weather:size=30}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5dp}$font$color
${color yellow}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5t}
${voffset 10}${color cyan}${hr 1} $color

```

the **.PL** file (with Spanish display)
```

#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update $file if set to 0 don't use $file

$spaces=" "; #spacing between each high low.
$fspaces=" "; #spacing between condition symbols.
$dspaces="   "; #spacing between day names.
$lines="\n\n\n\n"; #each \n represents one line between the days and temps

$Text::Wrap::columns = 55;
$initial_tab="\t\t\t "; #tab before first line in weather output
$subsequent_tab="\t\t "; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Sensación Térmica:  $tmf$degree\n";
					print "Humedad:    $hmt%\n"; 
					print "Viento:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #how many days are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		my $count=0;
		my $day=(split "t", $what)[0]; #how many days are we looking for
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]dt$/ {
		&file_op; #save weather to $file
		my $count1 = my $count2=0;
		my $day=(split "dt", $what)[0]; #how many days are we looking for
		my $flag=1; #print days once
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if(/<th>(\b.+\b)<\/th>/ && ++$count1<=$day){ #look for the conditions upto specified day
				$days[$count1-1]=$1; #save day
				&day_space($days);
			}
			elsif($high=~/\d+/ && $low=~/\d+/ && ++$count2<=$day){$ttext.=$high.$degree."/".$low.$degree.$spaces;}
			elsif($count1>=$day && $count2>=$day){print "$dtext\n$lines$ttext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		&usage; #print usage error
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size >= 1000){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub usage { #if correct options haven't been passed usage error
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-5]dt displays high/low temp in chosen system and then days up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	$ctext.=$_.$fspaces;
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_=" Hoy   ";}
	elsif ($_ =~ "Tonight"){$_=" Noc   ";}
	elsif ($_ =~ "Tomorrow"){$_="Mañ ";}
	elsif ($_ =~ "Thu"){$_="    Jue ";}
	elsif ($_ =~ "Fri"){$_="    Vie ";}
	elsif ($_ =~ "Sat"){$_="    Sab ";}
	elsif ($_ =~ "Sun"){$_="    Dom ";}
	elsif ($_ =~ "Mon"){$_="    Lun ";}
	elsif ($_ =~ "Tue"){$_="    Mar ";}
	elsif ($_ =~ "Wed"){$_="    Mié ";}
	$dtext.=$_.$dspaces;
}

```

---

### Post by Nythain on 2008-02-15
> **maxehhh said:**
> any idea why the font in the 5 day forecast is not right?

[IMG]http://img136.imageshack.us/img136/6664/weatherxp5.jpg[/IMG]
if its teh condition symbols, you coudl try changing the spacing in the actual script... i found that to get it as close to good as i can, i needed to manipulated the spacings more than the actual font sizings

---

### Post by maxehhh on 2008-02-15
Bryce M. i tried yours but no font (pics) comes up, saved ~/scripts/w-days.pl and started conky but nothing. Here's a screen.

[img]http://img258.imageshack.us/img258/8213/screenshotza3.jpg[/img]

btw... i use 1280x1024 too.

---

### Post by Bruce M. on 2008-02-15
> **maxehhh said:**
> Bryce M. i tried yours but no font (pics) comes up, saved ~/scripts/w-days.pl and started conky but nothing. Here's a screen.

[img]http://img258.imageshack.us/img258/8213/screenshotza3.jpg[/img]

btw... i use 1280x1024 too.

Ouch!  After saving w-days.pl did you make it executable?

```
sudo chmod a+x ~/scripts/w-days.pl
```

Bruce

---

### Post by aonegodman on 2008-02-16
> **Bruce M. said:**
> I have a screen resolution of: 1280 x 1024.  If you have that you can try mine:

the **.PL** file (with Spanish display)


muy bueno, señor!   :lol:

I knew you were up to something amigo.

---

### Post by Bruce M. on 2008-02-17
> **aonegodman said:**
> muy bueno, señor!   :lol:

I knew you were up to something amigo.

I was off the computer for a week or so (personal reasons), I also have Gusty running, I'm back and ironing out a few kinks from upgrading.  :)

---

### Post by jjgomera on 2008-02-17
> **Bruce M. said:**
> 

the **.PL** file (with Spanish display)]
muchas gracias por la traducción, llevaba un rato configurandolo y era desastroso

---

### Post by Bruce M. on 2008-02-17
> **jjgomera said:**
> muchas gracias por la traducción, llevaba un rato configurandolo y era desastroso

De nada.
You're welcome

GUSTS ... es ráfaga creo que.
GUSTS ... is ráfaga I believe.

Hay palabras que no puedo traducir proque estan en la página de web como:
There are some words I can't translate because they are in the webpage like

CONDICIONES: Partly Cloudy, Sunny, Thunderstorms, etc
PRESIÓN: 1012.9 hPa - steady - falling - rising

Tengas un buen día
Have a nice day
Bruce

---

### Post by hihihi on 2008-02-19
hi Bruce M., in your thumbnail i can read in spanish sunrise and sunset, which i can not find back in the script u attached, so tell me, how did u solve that?
i want to display sunset and sunrise, i am trying myself but till now with no success... any suggestion? thanks in advance

---

### Post by hihihi on 2008-02-19
here's how mine looks for now,
how can i change the spacing between High/Low temp?
i figured it out, BUT its unregular, why?
thx

oh btw: foggy is not included in the .pl so i added to it, where i live u need foggy. its letter "F"

> sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	elsif ($_ =~ "Foggy"){$_="F";}
	$ctext.=$_.$fspaces;
}


---

### Post by lvleph on 2008-02-19
> **hihihi said:**
> here's how mine looks for now,
how can i change the spacing between High/Low temp?
i figured it out, BUT its unregular, why?
thx

oh btw: foggy is not included in the .pl so i added to it, where i live u need foggy. its letter "F"

I added foggy a couple days ago as cloudy, which obviously is not a good solution. I just didn't see any other symbol that worked for it. The sunrise and sunset that Bruce has is from a different script. It could be added though. Maybe when I have time.

---

### Post by Cammy on 2008-02-19
> **hihihi said:**
> here's how mine looks for now,

Wow, Thursday calls for gamma radiation!  Yikes!

---

### Post by Crinos512 on 2008-02-19
> **Cammy said:**
> Wow, Thursday calls for gamma radiation!  Yikes!

ROTFL

---

### Post by Bruce M. on 2008-02-20
Help Please.

A little history
[LIST]
[*]Everything regarding Conky worked well in Feisty
[*]Installed Gutsy
[*]Set Metacity as default in Configuration Editor
[/LIST]

[CENTER]
[[IMG]http://img90.imageshack.us/img90/6981/whated0.th.png[/IMG]](http://img90.imageshack.us/my.php?image=whated0.png)
[/CENTER]

Questions:
[LIST=1]
[*]How can I have a syntax error on line 4 of a three line script?
[*]Why is permission denied?
[/LIST]

---

### Post by Nythain on 2008-02-20
Question 1
i would remove the && from the last line of the file... i think its expecting to run something else, and there's nothing else there on line 4, so syntax error.
here's an example of mine
```

#!/bin/bash
gnome-terminal --window-with-profile=transterm --geometry=47x16+1175+260 --execute ncmpc --port=6600 &
sleep 3 &
gnome-terminal --window-with-profile=transterm --geometry=47x19+1175+625 &
sleep 3 &
conky -c .weather &
sleep 3 &
conky -c .gmail &
sleep 3 &
conky -c .disks &
sleep 3 &
conky -c .system

```
Question 2
i have no idea why you have permission denied, thats just plain wonky

---

### Post by Bruce M. on 2008-02-20
> **Nythain said:**
> Question 1
i would remove the && from the last line of the file... i think its expecting to run something else, and there's nothing else there on line 4, so syntax error.

```
#!/bin/bash
sleep 20 &&
conky -c ~/.conkyscripts/conkymain
```

Worked with a "***new feature***" - conky disappeared when I closed the terminal

```
#!/bin/bash
sleep 20 &&
conky -c ~/.conkyscripts/conkymain &
```

Works great!
Strange, the **&&** was working fine in Feisty, just not in Gutsy.

Another "*new feature*" in Gutsy - can't **autostart** conky.
Lets see if that has been "disabled" and conky will start.   :)

> **Nythain said:**
> Question 2
i have no idea why you have permission denied, thats just plain wonky
My feelings too!
Bruce

---

### Post by lvleph on 2008-02-20
> **Bruce M. said:**
> ```
#!/bin/bash
sleep 20 &&
conky -c ~/.conkyscripts/conkymain
```

Worked with a "***new feature***" - conky disappeared when I closed the terminal

```
#!/bin/bash
sleep 20 &&
conky -c ~/.conkyscripts/conkymain &
```

Works great!
Strange, the **&&** was working fine in Feisty, just not in Gutsy.

Another "*new feature*" in Gutsy - can't **autostart** conky.
Lets see if that has been "disabled" and conky will start.   :)


My feelings too!
Bruce
Just add conky to the the session and it should load automatically when you start.

---

### Post by Bruce M. on 2008-02-20
> **lvleph said:**
> Just add conky to the the session and it should load automatically when you start.

Had that done in Feisty and it worked fine.
Now I see:
[CENTER]
[[IMG]http://img127.imageshack.us/img127/6463/screenshotou8.th.png[/IMG]](http://img127.imageshack.us/my.php?image=screenshotou8.png)
[/CENTER]
a little black square in the upper right, conky starts, background coveres it.

So I set sleep (now back at 20) as high as 120 seconds in steps of +30.  No luck, desktop covers it.

I know it's running because a:
```
killall conky
```
doesn't result in:
```
bruloo@bruloo:~$ killall conky
conky: no process killed
bruloo@bruloo:~$ 

```
I see:
```
bruloo@bruloo:~$ killall conky
bruloo@bruloo:~$ 

```

and once everything is setup and running if I:
```
bruloo@bruloo:~$ ./.startconky
bruloo@bruloo:~$ Conky: desktop window (10000bd) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2e00001)
Conky: drawing to double buffer

```
everything is just fine.

Just no ***autostart***

---

### Post by Nythain on 2008-02-20
Ok...

First, thanks bruce for solving my closing when i close the terminal problem... im retarded

Second, bruce totally isnt making things up... gutsy just doesnt like autostarting conky, we brought it up in another thread i think... i thought it was just compiz messing with it, but aparently its not... really cant just add the conky to the session... its weird, wich is why i have a startconky script also... unfortunately its the only work around i've managed to come up with, but im not familiar enough with gnome and its session manager to figure out how to make it autostart conky after EVERYTHING else :(

---

### Post by lvleph on 2008-02-20
Oh I see. I do use a conky script to start conky.

---

### Post by Bruce M. on 2008-02-20
> **Nythain said:**
> Ok...

First, thanks bruce for solving my closing when i close the terminal problem... im retarded

Second, bruce totally isnt making things up... gutsy just doesnt like autostarting conky, we brought it up in another thread i think... i thought it was just compiz messing with it, but aparently its not... really cant just add the conky to the session... its weird, wich is why i have a startconky script also... unfortunately its the only work around i've managed to come up with, but im not familiar enough with gnome and its session manager to figure out how to make it autostart conky after EVERYTHING else :(

I'm not convinced that it was compiz, even thought I now have it GONE!  But Gutsy is faster on this old PC without compiz, that I can't use anyway.  Even set at NONE for effects it chewed up memory.

Applications>System Tools>Configuration Editor
Select: >desktop > gnome > applications > window_manager

then right-click on:

current - change to: /usr/bin/metacity
default - change to: /usr/bin/metacity

It's the only way I found to disable compiz.

```
metacity --replace
```
did NOT work for me.

Try it and check with the Config Editor, compiz will still be there.

Anyway with metacity all is well here and conky auto-starting fine from Sessions:

Name: Conky
Command: /home/bruloo/.startconky

Bruce

---

### Post by Bruce M. on 2008-02-20
> **hihihi said:**
> hi Bruce M., in your thumbnail i can read in spanish sunrise and sunset, which i can not find back in the script u attached, so tell me, how did u solve that?
i want to display sunset and sunrise, i am trying myself but till now with no success... any suggestion? thanks in advance

Hi hihihi

Do you want it in Spanish or English?

Either way it's not from the **weather.pl** file from here.
It's from the standard way of getting weather using a weather.**sh** file and **xslt**.
Check out my [HowTo]("http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489")

If you want it in Spanish let me know.

---

### Post by Bruce M. on 2008-02-20
> **Cammy said:**
> Wow, Thursday calls for gamma radiation!  Yikes!

Maybe it's because of the Full Moon Eclipse.  :lolflag:

---

### Post by Cammy on 2008-02-21
> **Bruce M. said:**
> Maybe it's because of the Full Moon Eclipse.  :lolflag:

I originally thought that symbol was calling for a supernova of the sun, until I noticed there was a Friday forecast, which a supernova would preclude.

---

### Post by Bruce M. on 2008-02-21
> **Cammy said:**
> I originally thought that symbol was calling for a supernova of the sun, until I noticed there was a Friday forecast, which a supernova would preclude.

Ok, no supernovas allowed on Fridays, how about Thunder and Lightning on Sab?

---

### Post by noremac on 2008-02-22
Hmm, I intentionally go to a friends place to fix his conky up with this weather script. And when I get back I have the following. Before I left, I simply copied my conky script so I could use a bit of it at his. But even if I messed the conky script up (which I am darn sure I didn't) it would have had to have been restarted in order to take any effect right? I know it hasn't been restarted until now as I have been messing with it. 

Here's part of my .conkyrc containing the weather stuffs:
```
${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS - Huntsville TX
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl USTX0629 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl USTX0629 f t}
${voffset -15}$alignr${offset -60}${font weather:size=40}${execi 3600 perl ~/scripts/weather.pl USTX0629 f cp}$font
${voffset -10}${color1}$hr
${voffset -3}$alignc 4 DAY FORECAST 
${voffset -7}$hr $color

${font weather:size=40}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 4dp}${font}$color
${voffset -55}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 4dt}
${font HandelGotD:size=7}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 5w}${font}
```

Could this be some sort of problem from the information it is recieving from the interwebs? You can see its trying to display more than one weather icon. Lemme know of any suggestions, 

Thanks for any help,
-Cameron

---

### Post by lvleph on 2008-02-22
What was the forecast suppose to be? And do you have the latest script? That looks like it didn't know what to put for the forecast, because it didn't have the sybol encoded. If I knew what the forecast was suppose to be I could figure out what the problem was. I can see that the output is the html code from weather.com, but I don't know the forecast.

Next time you see an issue like that open terminal and then
```
cd ~/scripts
weather <city code> <system> cp
```
Then paste the output here, so I can figure out the problem.

---

### Post by imon9 on 2008-02-22
i got a question:

why is that everytime i start conky, it show a different size? since that happened, the alligmnent always messed up... help :(

---

### Post by noremac on 2008-02-22
> **lvleph said:**
> What was the forecast suppose to be? And do you have the latest script? That looks like it didn't know what to put for the forecast, because it didn't have the sybol encoded. If I knew what the forecast was suppose to be I could figure out what the problem was. I can see that the output is the html code from weather.com, but I don't know the forecast.

Next time you see an issue like that open terminal and then
```
cd ~/scripts
weather <city code> <system> cp
```
Then paste the output here, so I can figure out the problem.

Well, I recopied the weather.pl script from the changable settings on down and it seems to have taken care of it. Kind of weird. We'll see if that takes care of it entirely. I know though I didn't open that file before I left lastnight. Just copied my .conkyrc file. 

Thanks for the help,
-Cameron

---

### Post by Bruce M. on 2008-02-22
> **imon9 said:**
> i got a question:

why is that everytime i start conky, it show a different size? since that happened, the alligmnent always messed up... help :(

Show us your conky files that you are using.

---

### Post by imon9 on 2008-02-22
> **Bruce M. said:**
> Show us your conky files that you are using.

here you go :
```

# UBUNTU-CONKY.
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes
update_interval 3.0
# Minimum size of text area
# minimum_size 250 5
draw_shades no
draw_outline no # amplifies text if yes
draw_borders no
draw_graph_borders no
use_xft yes
xftalpha 1.0
xftfont Candera:size=6
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

TEXT
${color1}
${voffset -3}$alignc SYSTEM
${voffset -7}$hr $color

$nodename $sysname 
$kernel
CPU Temp: ${acpitemp}

${color1}
${voffset -3}$alignc NETWORK IP ${addr eth1}
${voffset -7}$hr $color

Down: $color${downspeed eth1} k/s ${alignr}Up: ${upspeed eth1} k/s$color
Total: ${totaldown eth1} ${alignr}Total: ${totalup eth1}
Inbound: ${tcp_portmon 1 32767 count}${alignr}Outbound: ${tcp_portmon 32768 
61000 count}

${color1}
${voffset -3}$alignc MOSCOW WEATHER
${voffset -7}$hr $color

${execi 3600 perl ~/.scripts/weather.pl RSXX0063 c w}${voffset -30}$alignr${offset -60}${execi 3600 perl ~/.scripts/weather.pl RSXX0063 c t}${voffset -10}$alignr${offset -60}${font weather:size=50}${execi 3600 perl ~/.scripts/weather.pl RSXX0063 c cp}$font

${font weather:size=35}${execi 3600 perl ~/.scripts/weather.pl RSXX0063 c 5dp}$font
${voffset -65}${execi 3600 perl ~/.scripts/weather.pl RSXX0063 c 5dt}

```

---

### Post by Bruce M. on 2008-02-22
> **imon9 said:**
> here you go :

```
# override_utf8_locale yes
```

Try that and see what happens.
REM it out with an #

Also your can you show us a screenshot?

---

### Post by noremac on 2008-02-23
Thought I solved my problem, however I got another. 

Now the weather is showing sunny for night time. It shows Tonight will be sunny, and that it is currently sunny. However I look out my window and its clearly dark. Thats with even a brand new script, straight from this thread. 
Any idea what would cause that?

Here is my .conkyrc, with weather at the very bottom:
```
background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 250
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 0
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes

TEXT
$sysname $kernel on $machine
Uptime $alignr $uptime
Load $alignr $loadavg

NETWORK ${hr 2}
Down: ${downspeed eth0} Kb/s ${alignr}Up: ${upspeed eth0} Kb/s
${downspeedgraph eth0 30,120} ${alignr}${upspeedgraph eth0 30,120}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}
${cpugraph cpu0}

MEM              ${alignr}CPU%     MEM%
 ${top_mem name 1}${alignr}${top_mem cpu 1}    ${top_mem mem 1}
 ${top_mem name 2}${alignr}${top_mem cpu 2}    ${top_mem mem 2}
 ${top_mem name 3}${alignr}${top_mem cpu 3}    ${top_mem mem 3}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS - Huntsville TX
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl USTX0629 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl USTX0629 f t}
${voffset -15}$alignr${offset -60}${font weather:size=40}${execi 3600 perl ~/scripts/weather.pl USTX0629 f cp}$font
${voffset -10}${color1}$hr
${voffset -3}$alignc 4 DAY FORECAST 
${voffset -7}$hr $color

${font weather:size=40}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 4dp}${font}$color
${voffset -55}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 4dt}
${font HandelGotD:size=7}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 5w}${font}
```

Perhaps I will wake up in the morning and it will have caught up with itself or something. We'll see...

Appreciate the help,
-Cameron

---

### Post by imon9 on 2008-02-23
i' ve solved my font problem too, but by adding the size of my font to 8 instead of 6....and did some extra alignment with the voffset etc

anyway, i do have other questions:
(1) I've used the commant weather.pl AB12345 c w1 but the description still uses english system in the report....what is wrong? 

(2) is there a way to change weather.pl script to show "c w1" using comma instead of a collumn...like this "today**,** the temperature..." instead of "today**:** the temparature..."

(3) and yeah..using the autostart script...i set it to 15 sec, sometimes works, sometimes dont...but set it to 60sec seem too long, no?

---

### Post by lvleph on 2008-02-23
> **noremac said:**
> Thought I solved my problem, however I got another. 

Now the weather is showing sunny for night time. It shows Tonight will be sunny, and that it is currently sunny. However I look out my window and its clearly dark. Thats with even a brand new script, straight from this thread. 
Any idea what would cause that?

Here is my .conkyrc, with weather at the very bottom:
```
background yes
use_xft yes
xftfont HandelGotD:size=9
xftalpha 0.5
update_interval 1.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 200 5
maximum_width 250
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders no
default_color white
default_shade_color red
default_outline_color green
alignment top_right
gap_x 10
gap_y 0
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes

TEXT
$sysname $kernel on $machine
Uptime $alignr $uptime
Load $alignr $loadavg

NETWORK ${hr 2}
Down: ${downspeed eth0} Kb/s ${alignr}Up: ${upspeed eth0} Kb/s
${downspeedgraph eth0 30,120} ${alignr}${upspeedgraph eth0 30,120}$color
Total: ${totaldown eth0} ${alignr}Total: ${totalup eth0}

$processes processes ($running_processes running)

CPU $alignr ${cpu cpu0}%
${cpubar cpu0}
${cpugraph cpu0}

MEM              ${alignr}CPU%     MEM%
 ${top_mem name 1}${alignr}${top_mem cpu 1}    ${top_mem mem 1}
 ${top_mem name 2}${alignr}${top_mem cpu 2}    ${top_mem mem 2}
 ${top_mem name 3}${alignr}${top_mem cpu 3}    ${top_mem mem 3}

MEM $alignc $mem / $memmax $alignr $memperc%
$membar

swap $alignc $swap / $swapmax $alignr $swapperc%
${swapbar}

${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS - Huntsville TX
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl USTX0629 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl USTX0629 f t}
${voffset -15}$alignr${offset -60}${font weather:size=40}${execi 3600 perl ~/scripts/weather.pl USTX0629 f cp}$font
${voffset -10}${color1}$hr
${voffset -3}$alignc 4 DAY FORECAST 
${voffset -7}$hr $color

${font weather:size=40}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 4dp}${font}$color
${voffset -55}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 4dt}
${font HandelGotD:size=7}${execi 3600 perl ~/scripts/weather.pl USTX0629 f 5w}${font}
```

Perhaps I will wake up in the morning and it will have caught up with itself or something. We'll see...

Appreciate the help,
-Cameron
Clear shows up as sunny. That is because the weather font doesn't have anything for clear at night. I suppose one of the moons could work...

---

### Post by tad1073 on 2008-02-23
How do I fix the spacing of the weather fonts?

---

### Post by lvleph on 2008-02-23
> **tad1073 said:**
> How do I fix the spacing of the weather fonts?

From the directions
> There are several different variables in the weather.pl script that are used in formatting. Spaces between each day's temps are controlled with the variables $leadingspace and $trailingspace (lines 17 and 18 ). There is also a variable for the spacing between each condition symbol, $fspaces (line 19). The spaces between each day can be controlled with the $dspaces variable (line 20). The number of lines between the days and temps, using the [1-5]dt option, can be controlled using the $lines variable (line 21), each /n represents one line.

---

### Post by tad1073 on 2008-02-23
\n changes the horizontil spacing, which I mean, it puts each condition symbols on a new line. It doesn't change the vertical spacing.

---

### Post by lvleph on 2008-02-23
Okay, I didn't understand what you meant. I thought you meant spacing between each icon. Vertical spacing is controlled within your conkyrc using ${valign} variable. There is a number in there that you will want to play around with.

---

### Post by tad1073 on 2008-02-23
Instead of dislaying "Tonight and Tommorow" what can i do to dislay "Sat, Sun, Mon" etc

---

### Post by Bruce M. on 2008-02-24
> **tad1073 said:**
> Instead of dislaying "Tonight and Tommorow" what can i do to dislay "Sat, Sun, Mon" etc

Today/Tonight and Tomorrow are variables drawn from the weather site, they do not identify it as anything else..

If they did, Sat Sun Mon would be the normal thing.

EDIT:  But lvleph did it anyway  :)

---

### Post by tad1073 on 2008-02-24
```
# Conky configuration
#
# the list of variables has been removed from this file in favour
# of keeping the documentation more maintainable.
# Check http://conky.sf.net for an up-to-date-list.
#
# The additions to this config require curl and xsltproc be installed

# set to yes if you want Conky to be forked in the background
background yes

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
xftfont Veranda:size=8

# Text alpha when using Xft
xftalpha 0.8

# Print everything to stdout?
# out_to_console no

# MPD host/port
# mpd_host localhost
# mpd_port 6600
# mpd_password tinker_bell

# Print everything to console?
# out_to_console no

# mail spool
mail_spool $MAIL

# Update interval in seconds
update_interval 1.0

# This is the number of times Conky will update before quitting.
# Set to zero to run forever.
total_run_times 0

# Create own window instead of using desktop (required in nautilus)
own_window yes

# If own_window is yes, you may use type normal, desktop or override
own_window_type normal

# Use pseudo transparency with own_window?
own_window_transparent yes

# If own_window_transparent is set to no, you can set the background colour here
own_window_colour hotpink

# If own_window is yes, these window manager hints may be used
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# Max window size
maximum_width 310

# Minimum size of text area
minimum_size 280 5

# Draw shades?
draw_shades no

# Draw outlines?
draw_outline no

# Draw borders around text
draw_borders no

# Draw borders around graphs
draw_graph_borders yes

# Stippled borders?
stippled_borders 0

# border margins
border_margin 4

# border width
border_width 1

# Default colors and also border colors
default_color lightgrey
default_shade_color grey
default_outline_color grey

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
#alignment none

# Gap between borders of screen and text
# same thing as passing -x at command line
#gap_x 5
#gap_y 5

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

#   mldonkey_hostname     Hostname for mldonkey stuff, defaults to localhost
#   mldonkey_port         Mldonkey port, 4001 default
#   mldonkey_login        Mldonkey login, default none
#   mldonkey_password     Mldonkey password, default none

# boinc (seti) dir
# seti_dir /opt/seti

# Allow for the creation of at least this number of port monitors (if 0 or not set, default is 16) 
#min_port_monitors 16

# Allow each port monitor to track at least this many connections (if 0 or not set, default is 256)
#min_port_monitor_connections 256

# none, xmms, bmp, audacious, infopipe (default is none)
#xmms_player none

# variable is given either in format $variable or in ${variable}. Latter
# allows characters right after the variable and must be used in network
# stuff because of an argument

# stuff after 'TEXT' will be formatted on screen
TEXT
${color #ffffff}${Font veranda:size=12}$TIME
${color1}${Font veranda:size=8}$hr
${voffset -3}$alignc CURRENT CONDITIONS 
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl 30127 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl 30127 f t}
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl 30127 f cp}$font
${voffset -10}${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST 
${voffset -7}$hr $color

${font weather:size=55}${execi 3600 perl ~/scripts/weather.pl 30127 f 5dp}${font}$color
${voffset -75}${execi 3600 perl ~/scripts/weather.pl 30127 f 5dt}
${execi 3600 perl ~/scripts/weather.pl 30127 f 7w}
${color #ffffff}$hr
${voffset -3}$alignc SYSTEM
${voffset -7}$hr
${color #ffffff}Host:$color $nodename - $sysname $kernel $machine
${color #ffffff}Uptime:$color $uptime ${color #ffffff}- Load:$color $loadavg
${color #ffffff}${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'} ${color white}${freq_dyn}Mhz
${color #ffffff}Usage:${color #ffffff} ${color white}${cpu}% ${color #ffffff}${cpubar}
${color #ffffff}${cpugraph ffffff}
${color #ffffff}RAM Usage:$color $mem/$memmax $color ${alignc}$memperc% ${color #ffffff}${membar}
${color #ffffff}Swap Usage:$color $swap/$swapmax $color ${alignc}$swapperc% ${color #ffffff}${swapbar}
${color #ffffff}Processes:$color $processes  ${color #ffffff}Running:$color $running_processes
${color #ffffff}Mini-top:
${color}Name: ${alignr 85} PID  ${alignr 40}CPU% ${alignr}MEM%
${color white}${top name 1} ${alignr 85} ${top pid 1} ${alignr 50}${top cpu 1} $alignr${top mem 1}
$color ${top name 2} ${alignr 85} ${top pid 2} ${alignr 50}${top cpu 2} $alignr${top mem 2}
$color ${top name 3} ${alignr 85} ${top pid 3} ${alignr 50}${top cpu 3} $alignr${top mem 3}
$color ${top name 4} ${alignr 85} ${top pid 4} ${alignr 50}${top cpu 4} $alignr${top mem 4}

${color #ffffff}Mem usage:
${color white} ${top_mem name 1} ${alignr 85} ${top_mem pid 1} ${alignr 50}${top_mem cpu 1} $alignr${top_mem mem 1}
$color ${top_mem name 2} ${alignr 85} ${top_mem pid 2} ${alignr 50}${top_mem cpu 2} $alignr${top_mem mem 2}
$color ${top_mem name 3} ${alignr 85} ${top_mem pid 3} ${alignr 50}${top_mem cpu 3} $alignr${top_mem mem 3}

${color #ffffff}File systems:
$color / ${alignc}${fs_used_perc /}% ${color #ffffff}${fs_bar /}
$color /home ${alignc}${fs_used_perc /home}% ${color #ffffff}${fs_bar /home}
$color /sdc1 ${alignc}${fs_used_perc /media/sdc1}% ${color #ffffff}${fs_bar /media/sdc1}

${color #ffffff}Networking:$color${wireless_bitrate ath0}${alignr}${color #ffffff}IP Address: $color${addr ath0}
 ${color #ffffff}Down:$color ${downspeed wifi0} k/s ${offset 80}${color #ffffff}Up:$color ${upspeed ath0} k/s
${color #ffffff}${downspeedgraph wifi0 20,155 ffffff} ${color #ffffff}${upspeedgraph ath0 20,155 ffffff }
${color #ffffff}Active Port(s):
${color #ffffff}Inbound Connection ${alignr} Local Service/Port${color white}
 ${tcp_portmon 1 32767 rhost 0} ${alignr} ${tcp_portmon 1 32767 rip 0}
 ${tcp_portmon 1 32767 rhost 1} ${alignr} ${tcp_portmon 1 32767 rip 1}
 ${tcp_portmon 1 32767 rhost 2} ${alignr} ${tcp_portmon 1 32767 rip 2}
${color #ffffff}Outbound Connection ${alignr} Local Service/Port${color white}
 ${tcp_portmon 32768 65535  rhost 0} ${alignr} ${tcp_portmon 32768 65535 rip 0}
 ${tcp_portmon 32768 65535 rhost 1} ${alignr} ${tcp_portmon 32768 65535 rip 1}
 ${tcp_portmon 32768 65535 rhost 2} ${alignr} ${tcp_portmon 32768 65535 rip 2}
```

---

### Post by lvleph on 2008-02-24
You could change the tonight and tomorrow, by changing the script. You would want to use the time function and a regular expression to replace those words with the actual day.

EDIT: More specifically, you would change the code in the day_space function (lines 247 - 259).

---

### Post by lvleph on 2008-02-24
> **imon9 said:**
> i' ve solved my font problem too, but by adding the size of my font to 8 instead of 6....and did some extra alignment with the voffset etc

anyway, i do have other questions:
(1) I've used the commant weather.pl AB12345 c w1 but the description still uses english system in the report....what is wrong? 

(2) is there a way to change weather.pl script to show "c w1" using comma instead of a collumn...like this "today**,** the temperature..." instead of "today**:** the temparature..."

(3) and yeah..using the autostart script...i set it to 15 sec, sometimes works, sometimes dont...but set it to 60sec seem too long, no?

The w function will always show in imperial. The reason is, because weather.com only shows the descriptions in imperial. I think it is pretty lame, but there is not much I can do about it. Actually that is not the truth. I can do conversions, but it will take me some time to figure out exactly what to do. It is not exactly straight forward. The conversion is but finding what to convert and what I am converting from and to what I should convert to is not.

To change the colon to a comma you will need to change line 147 of the code. You will need to know regular expressions to do it. However, you can just replace
```
(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
```
with
```
(my $when) = /<li><strong>(\b.+\b)\:<\/strong>/.",";
```
I believe that will work.

I set my autostart to 30secs. Works unless I am connecting to a network I haven't connected to before.

EDIT: Using awk to change the colon would be better than changing the script, because then you want to change it each time you get the newest version. Look up how to use awk. The command would look something like this
```
${execi 3600 perl ~/scripts/weather.pl <citycode> <system> w5 | awk <pattern>}
```

---

### Post by tad1073 on 2008-02-24
I abbreviated today, tonight and tomorrow in the script which worked for alignment w/ the weather fonts, but the high/low was off.

I don't know java script.

---

### Post by lvleph on 2008-02-24
It's not java, so that wouldn't help you; it's Perl. Refer back to my previous post on your alignment issue and the original directions for alignment to figure out alignment issues. All the issues have been already addressed in those posts. If you don't understand them, let me know which part you don't understand and I can walk you through it.

---

### Post by lvleph on 2008-02-24
Give me a few minutes and I will write the code you will need to display the day instead of today, tonight, or tomorrow.

---

### Post by lvleph on 2008-02-24
replace lines 247-259 with the following. 
```
sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today" || $_ =~  "Tonight"){
		$day=localtime(time)[6];
		if($day==0){$_="   Sun  ";}
		elsif($day==1){$_="   Mon  ";}
		elsif($day==2){$_="   Tue  ";}
		elsif($day==3){$_="   Wed  ";}
		elsif($day==4){$_="   Thu  ";}
		elsif($day==5){$_="   Fri  ";}
		elsif($day==6){$_="   Sat  ";}
	}
	elsif ($_ =~ "Tomorrow"){
		$day=(localtime(time)[6]+1) % 7;
		if($day==0){$_="   Sun  ";}
		elsif($day==1){$_="   Mon  ";}
		elsif($day==2){$_="   Tue  ";}
		elsif($day==3){$_="   Wed  ";}
		elsif($day==4){$_="   Thu  ";}
		elsif($day==5){$_="   Fri  ";}
		elsif($day==6){$_="   Sat  ";}
	}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```
Remove any spacing you don't want. In fact, if you don't want any of the spacing you could get rid of all the code between the tomorrow section and $dtext. Before running it in conky, use the terminal and run the script using 
```
perl ~/scripts/weather.pl <citycode> <system> 5d
```
If there are any issues post them here.

---

### Post by tad1073 on 2008-02-24
that script didn't display anything.

```
r:~$ perl ~/scripts/weather.pl <citycode> <system> 5d
bash: syntax error near unexpected token `<'
```

---

### Post by Bruce M. on 2008-02-24
> **lvleph said:**
> replace lines 247-259 with the following. 
```
sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today" || $_ =~  "Tonight"){
		$day=localtime(time)[6];
		if($day==0){$_="   Sun  ";}
		elsif($day==1){$_="   Mon  ";}
		elsif($day==2){$_="   Tue  ";}
		elsif($day==3){$_="   Wed  ";}
		elsif($day==4){$_="   Thu  ";}
		elsif($day==5){$_="   Fri  ";}
		elsif($day==6){$_="   Sat  ";}
	}
	elsif ($_ =~ "Tomorrow"){
		$day=(localtime(time)[6]+1) % 7;
		if($day==0){$_="   Sun  ";}
		elsif($day==1){$_="   Mon  ";}
		elsif($day==2){$_="   Tue  ";}
		elsif($day==3){$_="   Wed  ";}
		elsif($day==4){$_="   Thu  ";}
		elsif($day==5){$_="   Fri  ";}
		elsif($day==6){$_="   Sat  ";}
	}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```
Remove any spacing you don't want. In fact, if you don't want any of the spacing you could get rid of all the code between the tomorrow section and $dtext. Before running it in conky, use the terminal and run the script using 
```
perl ~/scripts/weather.pl <citycode> <system> 5d
```
If there are any issues post them here.

I should have known that if there was a way, you'd find it.
Thanks for this, now to apply to my Spanish setup.  :)
Bruce

---

### Post by Bruce M. on 2008-02-24
Oopps!
```
bruloo@bruloo:~$ ./.startconky
bruloo@bruloo:~$ Conky: desktop window (1000035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2a00001)
Conky: drawing to double buffer
syntax error at /home/bruloo/scripts/w-days.pl line 248, near ")["
syntax error at /home/bruloo/scripts/w-days.pl line 258, near ")["
Execution of /home/bruloo/scripts/w-days.pl aborted due to compilation errors.
syntax error at /home/bruloo/scripts/w-days.pl line 248, near ")["
syntax error at /home/bruloo/scripts/w-days.pl line 258, near ")["
Execution of /home/bruloo/scripts/w-days.pl aborted due to compilation errors.
```

Other than day name changes and spacing the coding is the same:
**NOTE:** Line numbers added by me

```

246 sub day_space { #Adds spaces for aligment
247	if ($_ =~ "Today" || $_ =~  "Tonight"){
248		$day=localtime(time)[6];
249		if($day==0){$_="  Dom      ";}
259		elsif($day==1){$_="  Lun      ";}
251		elsif($day==2){$_="  Mar      ";}
252		elsif($day==3){$_="  Mie      ";}
253		elsif($day==4){$_="  Jue      ";}
254		elsif($day==5){$_="  Vie      ";}
255		elsif($day==6){$_="  Sab      ";}
256	}
257	elsif ($_ =~ "Tomorrow"){
258		$day=(localtime(time)[6]+1) % 7;
259		if($day==0){$_="Dom";}
260		elsif($day==1){$_="Lun";}
261		elsif($day==2){$_="Mar";}
262		elsif($day==3){$_="Mié";}
263		elsif($day==4){$_="Jue";}
264		elsif($day==5){$_="Vie";}
265		elsif($day==6){$_="Sab";}
266	}
267	elsif ($_ =~ "Thu"){$_="      Jue";}
268	elsif ($_ =~ "Fri"){$_="      Vie";}
269	elsif ($_ =~ "Sat"){$_="      Sab";}
270	elsif ($_ =~ "Sun"){$_="      Dom";}
271	elsif ($_ =~ "Mon"){$_="      Lun";}
272	elsif ($_ =~ "Tue"){$_="      Mar";}
273	elsif ($_ =~ "Wed"){$_="      Mié";}
274	$dtext.=$_.$dspaces;
275}
```

Any ideas why?

---

### Post by lvleph on 2008-02-24
> **tad1073 said:**
> that script didn't display anything.

```
r:~$ perl ~/scripts/weather.pl <citycode> <system> 5d
bash: syntax error near unexpected token `<'
```
Where you see <citycode> and <system> you are suppose replace it with your city code and preferred system.

---

### Post by lvleph on 2008-02-24
> **Bruce M. said:**
> Oopps!
```
bruloo@bruloo:~$ ./.startconky
bruloo@bruloo:~$ Conky: desktop window (1000035) is subwindow of root window (45)
Conky: window type - override
Conky: drawing to created window (2a00001)
Conky: drawing to double buffer
syntax error at /home/bruloo/scripts/w-days.pl line 248, near ")["
syntax error at /home/bruloo/scripts/w-days.pl line 258, near ")["
Execution of /home/bruloo/scripts/w-days.pl aborted due to compilation errors.
syntax error at /home/bruloo/scripts/w-days.pl line 248, near ")["
syntax error at /home/bruloo/scripts/w-days.pl line 258, near ")["
Execution of /home/bruloo/scripts/w-days.pl aborted due to compilation errors.
```

Other than day name changes and spacing the coding is the same:
**NOTE:** Line numbers added by me

```

246 sub day_space { #Adds spaces for aligment
247	if ($_ =~ "Today" || $_ =~  "Tonight"){
248		$day=localtime(time)[6];
249		if($day==0){$_="  Dom      ";}
259		elsif($day==1){$_="  Lun      ";}
251		elsif($day==2){$_="  Mar      ";}
252		elsif($day==3){$_="  Mie      ";}
253		elsif($day==4){$_="  Jue      ";}
254		elsif($day==5){$_="  Vie      ";}
255		elsif($day==6){$_="  Sab      ";}
256	}
257	elsif ($_ =~ "Tomorrow"){
258		$day=(localtime(time)[6]+1) % 7;
259		if($day==0){$_="Dom";}
260		elsif($day==1){$_="Lun";}
261		elsif($day==2){$_="Mar";}
262		elsif($day==3){$_="Mié";}
263		elsif($day==4){$_="Jue";}
264		elsif($day==5){$_="Vie";}
265		elsif($day==6){$_="Sab";}
266	}
267	elsif ($_ =~ "Thu"){$_="      Jue";}
268	elsif ($_ =~ "Fri"){$_="      Vie";}
269	elsif ($_ =~ "Sat"){$_="      Sab";}
270	elsif ($_ =~ "Sun"){$_="      Dom";}
271	elsif ($_ =~ "Mon"){$_="      Lun";}
272	elsif ($_ =~ "Tue"){$_="      Mar";}
273	elsif ($_ =~ "Wed"){$_="      Mié";}
274	$dtext.=$_.$dspaces;
275}
```

Any ideas why?

Give me a couple minutes. I messed up the code.

---

### Post by lvleph on 2008-02-24
Here you go.
```
sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today" || $_ =~  "Tonight"){
		$day=(localtime(time))[6];
		if($day==0){$_="   Sun  ";}
		elsif($day==1){$_="   Mon  ";}
		elsif($day==2){$_="   Tue  ";}
		elsif($day==3){$_="   Wed  ";}
		elsif($day==4){$_="   Thu  ";}
		elsif($day==5){$_="   Fri  ";}
		elsif($day==6){$_="   Sat  ";}
	}
	elsif ($_ =~ "Tomorrow"){
		$day=((localtime(time))[6]+1) % 7;
		if($day==0){$_="   Sun  ";}
		elsif($day==1){$_="   Mon  ";}
		elsif($day==2){$_="   Tue  ";}
		elsif($day==3){$_="   Wed  ";}
		elsif($day==4){$_="   Thu  ";}
		elsif($day==5){$_="   Fri  ";}
		elsif($day==6){$_="   Sat  ";}
	}
	elsif ($_ =~ "Thu"){$_="   Thu  ";}
	elsif ($_ =~ "Fri"){$_="   Fri  ";}
	elsif ($_ =~ "Sat"){$_="   Sat  ";}
	elsif ($_ =~ "Sun"){$_="   Sun  ";}
	elsif ($_ =~ "Mon"){$_="   Mon  ";}
	elsif ($_ =~ "Tue"){$_="   Tue  ";}
	elsif ($_ =~ "Wed"){$_="   Wed  ";}
	$dtext.=$_.$dspaces;
}
```

and for our Spanish speakers
```
sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today" || $_ =~  "Tonight"){
		$day=(localtime(time))[6];
		if($day==0){$_="   Dom  ";}
		elsif($day==1){$_="   Lun  ";}
		elsif($day==2){$_="   Mar  ";}
		elsif($day==3){$_="   Mié  ";}
		elsif($day==4){$_="   Jue  ";}
		elsif($day==5){$_="   Vie  ";}
		elsif($day==6){$_="   Sab  ";}
	}
	elsif ($_ =~ "Tomorrow"){
		$day=((localtime(time))[6]+1) % 7;
		if($day==0){$_="   Dom  ";}
		elsif($day==1){$_="   Lun  ";}
		elsif($day==2){$_="   Mar  ";}
		elsif($day==3){$_="   Mié  ";}
		elsif($day==4){$_="   Jue  ";}
		elsif($day==5){$_="   Vie  ";}
		elsif($day==6){$_="   Sab  ";}
	}
	elsif ($_ =~ "Thu"){$_="   Jue  ";}
	elsif ($_ =~ "Fri"){$_="   Vie  ";}
	elsif ($_ =~ "Sat"){$_="   Sab  ";}
	elsif ($_ =~ "Sun"){$_="   Dom  ";}
	elsif ($_ =~ "Mon"){$_="   Lun  ";}
	elsif ($_ =~ "Tue"){$_="   Mar  ";}
	elsif ($_ =~ "Wed"){$_="   Mié  ";}
	$dtext.=$_.$dspaces;
}
```

---

### Post by lvleph on 2008-02-24
I was trying to figure out how to make it multilingual, but I haven't figured that out yet.

---

### Post by Bruce M. on 2008-02-24
> **lvleph said:**
> I was trying to figure out how to make it multilingual, but I haven't figured that out yet.

Yea, that could be tricky, first you'd need to know every possible alternative answer to everything.

IE: Barometer: raising, steady, falling.

Take a look at the "Fun with Fonts" you had to add F for Fog, etc, etc,

If I knew how to do it ( Perl ) and what I was looking for in a webpage I'd be working on [this site]("http://www.smn.gov.ar/") for my own use.  Foe me it seems crazy that people here have to rely on a site in the US for weather, but the same applies for Europe and other geographical areas (Australia, Japan, New Zealand, where ever) as well.

But thanks for this code.

EDIT:
Other problems you'd run into (Spanish example) mañana means Tomorrow and Morning ... so:

Tomorrow morning = Mañana en la mañana
The key is: en **la** = in **the**

---

### Post by lvleph on 2008-02-24
I was looking for a multilingual site so that I could make it multilingual.

---

### Post by Bruce M. on 2008-02-24
> **lvleph said:**
> I was looking for a multilingual site so that I could make it multilingual.

OK, try Canada: English French
Switzerland - they have 5 official languages, popch might know of one I'll ask him.

Meantime I'll also look for a weather site in Canada and see what I come up with.

---

### Post by tad1073 on 2008-02-24
[QUOTE=lvleph;4396943]Where you see <citycode> and <system> you are suppose replace it with your city code and preferred system.[/QUOTE
thanks, it works great.

---

### Post by Bruce M. on 2008-02-24
@ lvleph

[Environment Canada]("http://www.weatheroffice.gc.ca/canada_e.html")

Really nice link near the bottom: Text only - French and English
(says World Weather too)

---

### Post by lvleph on 2008-02-24
@ Bruce

[World Weather](http://www.worldweather.org/)

I will look into this a bit.

---

### Post by Bruce M. on 2008-02-24
> **lvleph said:**
> @ Bruce

[World Weather](http://www.worldweather.org/)

I will look into this a bit.

Hey, nice but:

Just checked out Buenos Aires, 3 day forecast, but no current weather.  :(

---

### Post by lvleph on 2008-02-24
I think I will look into a different way to get the translations.

---

### Post by Bruce M. on 2008-02-24
> **lvleph said:**
> I think I will look into a different way to get the translations.

Also I just found the [Official Swiss]("http://www.swissinfo.ch/eng/weather/index.html?siteSect=450") site (English Only)  :(

---

### Post by Bruce M. on 2008-02-24
> **lvleph said:**
> I think I will look into a different way to get the translations.

I'm curious as to what translations you want?
English to what?

I wanted the Argintine site because it is here and what they use on the TV here.  Sometimes there is a 5°C difference from what I see in the google site I'm using now and what actually is going on here.  :(

How long would it take to learn perl?

---

### Post by lvleph on 2008-02-24
I couldn't tell you how long it would take you to learn.

---

### Post by Bruce M. on 2008-02-24
> **lvleph said:**
> I couldn't tell you how long it would take you to learn.

Hmm, 58 and going on 95, don't think I have the time  :(

---

### Post by Bruce M. on 2008-02-25
@ lvleph

Just heard from popch, here's his quick list:

[http://www.meteoschweiz.admin.ch/web/en/weather.html](http://www.meteoschweiz.admin.ch/web/en/weather.html) is as official as you get. Unfortunately, the forecasts are not available in English

[http://www.meteoblue.ch/](http://www.meteoblue.ch/) lets you select several languages (see top right of page)

[http://www.westwind.ch/](http://www.westwind.ch/) is a collection of weather related links; possibly useful, but then, perhaps not.

[http://www.ticino.ch/guardaTicino/meteo.jsp](http://www.ticino.ch/guardaTicino/meteo.jsp)

[http://meteo.search.ch/](http://meteo.search.ch/) also offers several languages; no forecasts in English, though

[http://my.meteoblue.com/my/](http://my.meteoblue.com/my/) Not really what you're looking for but worth a look, anyway

[http://www.meteonews.ch/index.php?se...er_peu&lang=en](http://www.meteonews.ch/index.php?se...er_peu&lang=en) Select language on top left of page (very small letters, may need to scroll up before visible)

Bruce

---

### Post by lvleph on 2008-02-25
The issue with using different sites for each language is that they are all formatted differently, and I would have to write a script for each one.

---

### Post by Bruce M. on 2008-02-25
> **lvleph said:**
> The issue with using different sites for each language is that they are all formatted differently, and I would have to write a script for each one.

Yea, I know.  :(

---

### Post by Bruce M. on 2008-02-26
It been a while since I've made any changes to my conky, other then tweaking text alignment in the weather.  What was 3 conkys at one time have been reduced to one.

So here's my "finished" conky:

[CENTER]
[[IMG]http://img240.imageshack.us/img240/108/screenshotqm4.th.jpg[/IMG]](http://img240.imageshack.us/my.php?image=screenshotqm4.jpg)
[/CENTER]

My conky file: **conkymain**
```

own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
own_window_colour black
double_buffer yes
use_spacer yes
use_xft yes
xftfont HandelGotD:size=8
xftalpha 0.5
update_interval 8.0
draw_shades no
draw_outline yes # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase
stippled_borders 3
border_margin 9
border_width 10
default_color white
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right
gap_x 10
gap_y 35
# Subtract file system buffers from used memory?
no_buffers yes
draw_outline yes
draw_shades yes
# shadecolor black
default_outline_color black
default_shade_color black

TEXT
${font :size=10}${alignc}${color cyan}~~== ${color orange}GMT ${color white}${tztime GMT %H:%M} ${color cyan}==~~$color
${alignc}${Color orange}~~== ${color cyan}Canada ${color orange}==~~$color$font
${color orange}Sis${alignr}${color cyan}Winnipeg${color cyan}: ${color white}${tztime Canada/Central %H:%M}$color
${color orange}JBM & CDM & LilSis${alignr}${alignr}${color cyan}London${color cyan}: ${color white}${tztime Canada/Eastern %H:%M}$color

${font :size=10}${alignc}${color cyan}~~== ${alignc}${color white}${exec whoami} @ $nodename ${color cyan}==~~$color$font
${alignc}${color orange}$sysname $kernel ($machine)$color
${font :size=20}${color white}${alignc}${time %H:%M}$color$font
${font :size=12}${color cyan}${alignc}${time %A, %d %b. %Y}$color$font
${color yellow}UpTime:${alignr}$uptime$color
${color cyan}${hr 1}$color
${color orange}System Temps:$color${alignr}(Low = 0°C / High = 127°C)
${color yellow}${execi 8 sensors | grep -A 1 'CPU Temp:' | cut -c0-19| sed '/^$/d'}$color
${color cyan}${hr 1}$color
${color orange}CPU:$color${execi 86400 cat /proc/cpuinfo | grep "model name" | cut -c13-37} ${cpu}% ${color orange}${cpubar cpu0}$color
${color cyan}Freq: ${color white}$freq ${color cyan}MHz${alignr}${color cyan}Running: ${color white}$running_processes ${color cyan}of ${color white}$processes${color cyan}processes $color
${color cyan}Load Avg (${color yellow}Min${color cyan}):$alignr${color yellow}1: ${color white}${loadavg 1}   ${color yellow}5: ${color white}${loadavg 2}   ${color yellow}15: ${color white}${loadavg 3} ${color orange}$color
${color orange}MEM: ${color cyan}RAM: ${color white}$memperc% ${color cyan}(${color white}${mem} ${color cyan}of ${color orange}${memmax}${color cyan}) ${color orange}$membar $color
${color cyan}Memory Buffered:${color white}${alignr 2}${buffers}$color
${color cyan}Memory Cached:${color white}${alignr 2}${cached}$color
${color orange}DISK: ${color cyan}Swap: ${color white}$swapperc% ${color cyan}(${color white}$swap ${color cyan}of ${color orange}${swapmax}${color cyan})${color orange} ${swapbar}$color
${color orange}HD Info ${color cyan}${hr 1}$color
${color cyan}/:${offset 35}${color white}${fs_free_perc /}%${alignr 2}${color cyan}$fs_free (${color white}${fs_used /} ${color cyan}of ${color orange}${fs_size /}${color cyan})$color
${color cyan}/home:${offset 3}${color white}${fs_free_perc /home/bruloo}%${alignr 2}${color cyan}$fs_free  (${color white}${fs_used /home/bruloo} ${color cyan}of ${color orange}${fs_size /home/bruloo}${color cyan})$color
${color cyan}40G:${offset 16}${color white}${fs_free_perc /media/sdb1}%${alignr 2}${color cyan}${fs_free /media/sdb1} (${color white}${fs_used /media/sdb1} ${color cyan}of ${color orange}${fs_size /media/sdb1}${color cyan})$color
${color cyan}W2K:${offset 13}${offset 2}${color white}${fs_free_perc /media/sda1}%${alignr 2}${color cyan}${fs_free /media/sda1} (${color white}${fs_used /media/sda1} ${color cyan}of ${color orange}${fs_size /media/sda1}${color cyan})$color
${color orange}WEATHER: ${color cyan}${hr 1}$color
${color cyan}Lat: ${color orange}34°35'00"S   ${color cyan}Long: ${color orange}58°21'00"W ${alignr} ${color cyan}Alt: ${color orange}25 m$color
${color gold}${execi 600 ~/scripts/sp-weather.sh ARBA0009}
${color cyan}${hr 1} $color
${color yellow}${alignc 18}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5dt}$color
${color cyan}${alignc 105}${voffset -50}${font weather:size=24}${execi 14400 perl ~/scripts/w-days.pl ARBA0009 c 5dp}$font$color
${voffset 15}${color cyan}${hr 1} $color
${color orange}IP:${alignc}${color white}${addr eth0}$color
${color cyan}Down: ${color white}${downspeed eth0}k/s ${alignr}${color cyan}Up: ${color white}${upspeed eth0}k/s $color
${color cyan}Total: ${color white}${totaldown eth0} ${alignr}${color cyan}Total: ${color white}${totalup eth0} $color
${color cyan}Inbound: ${color white}${tcp_portmon 1 32767 count}          ${color cyan}Outbound: ${color white}${tcp_portmon 32768 61000 count}${alignr}${color cyan}Total: ${color white}${tcp_portmon 1 65535 count} $color
${color orange}Connections: ${color white}${tcp_portmon 32768 61000 count} ${alignr} ${color orange}Service/Port $color${color white}
${tcp_portmon 32768 61000 rhost 0} ${alignr} ${tcp_portmon 32768 61000 rservice 0}
${tcp_portmon 32768 61000 rhost 1} ${alignr} ${tcp_portmon 32768 61000 rservice 1}
${tcp_portmon 32768 61000 rhost 2} ${alignr} ${tcp_portmon 32768 61000 rservice 2}
${tcp_portmon 32768 61000 rhost 3} ${alignr} ${tcp_portmon 32768 61000 rservice 3}
${tcp_portmon 32768 61000 rhost 4} ${alignr} ${tcp_portmon 32768 61000 rservice 4}
${tcp_portmon 32768 61000 rhost 5} ${alignr} ${tcp_portmon 32768 61000 rservice 5}$color

```
My **sp-weather.sh** to call my weather as seen between Desde and Luna Icon
```

#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# Modified by Vredfreak
# The orignal script and xslt can be downloaded from http://pondol.com/weather.tar.gz

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use http://xoap.weather.com/search/search?where=[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=ARBA0009

# s=standard units, m=metric units
UNITS=m

# where this script and the XSLT lives
RUNDIR=~/scripts

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at http://curl.haxx.se/
CURLCMD=/usr/bin/curl

# get it at http://xmlsoft.org/XSLT/
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?dayf=10&unit=$UNITS&cc=*"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/sp-weather.xslt

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"

#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"

```

and my **sp-weather.xslt** used by sp-weather.sh
```

<!-- 

 This XSLT is used to translate an XML response from the weather.com
 XML API. 

 You can format this file to your liking. Two things you may feel 
 like doing:

	1) Modify the layout of the fields or static text already defined
	2) Add other fields from the XML response file that aren't referenced in this
	   XSLT. You can grab a full list by just doing a: 
           wget "http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS" 
           (change $LOCID and $UNITS to suit your needs)
-->

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" > 
	<xsl:output method="text" disable-output-escaping="yes"/>
	<xsl:template match="weather">
			<xsl:apply-templates select="loc"/>
			<xsl:apply-templates select="cc"/>
			<!-- <xsl:apply-templates select="dayf/day[@d='1']"/> -->
	</xsl:template>
	
			<xsl:template match="loc">

<xsl:text>Desde:   </xsl:text><xsl:value-of select="dnam"/>
<!-- <xsl:text>
Lat: </xsl:text><xsl:value-of select="lat"/>
<xsl:text>                  Long: </xsl:text><xsl:value-of select="lon"/> -->
<xsl:text>
Salida del Sol: </xsl:text><xsl:value-of select="sunr"/>
<xsl:text>   Ocaso: </xsl:text><xsl:value-of select="suns"/>

			</xsl:template>

			<xsl:template match="cc">
<xsl:text>

Temp: </xsl:text><xsl:value-of select="tmp"/><xsl:value-of select="/weather/head/ut"/>

<xsl:text>      Sensación Térmica: </xsl:text><xsl:value-of select="flik"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text>

Condiciónes: </xsl:text><xsl:value-of select="t"/>
<xsl:text>
Vis: </xsl:text><xsl:value-of select="vis"/><xsl:text> KM</xsl:text>
<xsl:text>      Humedad: </xsl:text><xsl:value-of select="hmid"/><xsl:text>%</xsl:text>
<xsl:text>
Viento: </xsl:text>
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>0</xsl:text></xsl:when>
	<xsl:otherwise><xsl:value-of select="wind/s"/></xsl:otherwise>
</xsl:choose>
<xsl:value-of select="/weather/head/us"/> 
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>(0 km/h)</xsl:text></xsl:when>
	<xsl:otherwise><xsl:text> (</xsl:text><xsl:value-of select="round(wind/s * 0.6214)"/><xsl:text> mph)</xsl:text></xsl:otherwise>
</xsl:choose>
<xsl:text> (</xsl:text><xsl:value-of select="wind/t"/>
<xsl:text>)</xsl:text>
<xsl:text>
Ráfaga: </xsl:text><xsl:value-of select="wind/gust"/>
<xsl:text> km/h</xsl:text>
<xsl:text>
Presión: </xsl:text><xsl:value-of select="bar/r"/>
<xsl:text> hPa ~ </xsl:text><xsl:value-of select="bar/d"/>

<xsl:text>
UV: </xsl:text><xsl:value-of select="uv/i"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="uv/t"/>
<xsl:text>      Hr: </xsl:text><xsl:value-of select="dewp"/><xsl:text> C</xsl:text>

<xsl:text>

Luna Icon: </xsl:text><xsl:value-of select="moon/icon"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="moon/t"/>

	</xsl:template>

<!--	<xsl:template match="dayf/day[@d='1']">
<xsl:text>

DAY 02: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
 <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
	</xsl:template>

	<xsl:template match="dayf/day[@d='2']">
<xsl:text>
DAY 03: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> to </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
 <xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
	</xsl:template> -->

</xsl:stylesheet>

```

And last but not least my **w-days.pl** script for the 5 day forecast with the symbol weather fonts:
```

#!/usr/bin/perl

use Switch;
use Encode;
use Text::Wrap;


# This script was written by lvleph and inspired by the original conky weather script written by azhag (azhag@bsd.miki.eu.org)
# Modyfied by LazarusHC to list more details

$code=$ARGV[0]; #zipcode or weather.com city code
$system=$ARGV[1]; #f for imperial c for metric
$what=$ARGV[2]; #what are we looking for?
$file="/tmp/weather.html"; #temp holding weather
$update=3600; #time in seconds to update $file if set to 0 don't use $file

$spaces="   "; #spacing between each high low.
$fspaces="  "; #spacing between condition symbols.
$dspaces="   "; #spacing between day names.
$lines="\n\n\n"; #each \n represents one line between the days and temps

$Text::Wrap::columns = 55;
$initial_tab="\t\t\t "; #tab before first line in weather output
$subsequent_tab="\t\t "; #tab before each subsequet line in weather output

$degree= encode_utf8( "\x{00B0}" ); #give me the degree symbol, not everyone has same locale

#ensure user inputs proper system
if($system !=~ "c" || $system !=~ "f"){$what=0;} #this will give usage error 

switch($what){ #determine what user wants
	case "c" { #if current conditions
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cn2) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				if($cn2){print "$cn2\n"; exit;}			
			}
		}
	}
	case "w" { #if list
		&file_op; #save weather to file
		while(<FILE>){ #cycle through file
			if (/<dt>Feels Like:<\/dt>/ .. /<dd>/){ #found feels like temp
				($tmf) = /<dd>(-?\d+)/; #sav temp								
			}
			if (/<dt>Humidity:<\/dt>/ .. /<dd>/){ #found current humidity
				($hmt) = /<dd>(-?\d+)/; #save current humidity					
			}
			if (/<dt>Wind:<\/dt>/ .. /<dd>/){ #found wind conditions
				($wnd) = /<dd>(\b.+\b)<\/dd>/; #save wind conditions
				#do we have current conditions?
				if($tmf && $hmt && $wnd){
					print "Sensación Térmica:  $tmf$degree\n";
					print "Humedad:    $hmt%\n"; 
					print "Viento:        $wnd\n"; exit;}
			}
		}
	}	
	case "cp" { #if current conditions symbol
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<em>Current conditions/ .. /<h3>/){ #found current conditions
				($cnd) = /<h3>(\b.+\b)<\/h3>/; #save current conditions
				#do we have current conditions? Then translate into symbol
				if($cnd){cond_symb($cnd); print "\n"; exit;}
			}
		}
	}	
	case "t" { #if current temp
		&file_op; #save weather to $file
		while(<FILE>){ #cycle through file
			if (/<div id="forecast-temperature">/ .. /<h3>/){ #found current temp
				($tmp) = /<h3>(-?\d+)/; #save current temp
				#do we have current temp? Then print
				if($tmp){print "$1$degree\n"; exit;}
			}
		}
	}
	case /[1-5]d$/ { #display the days up to specified day 
		&file_op; #save weather to $file
		my $day=(split "t", $what)[0]; #how many days are we looking for
		my $count=0; 
		while(<FILE>){
			if(/<th>(\b.+\b)<\/th>/ && ++$count<=$day){ #look for the conditions upto specified day
				$days[$count-1]=$1; #save day
				&day_space($days);
			}
			elsif($count>=$day){print "$dtext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-5]dp$/ { #display the conditions from today through day $days
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #how many days are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count<=$day){ #look for the conditions upto specified day
				$cnd[$count-1]=$1; #save conditions
				&cond_symb ($cnd[$count-1]); #translate conditions to symbol
				#exit;
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]t$/ { #display the temps from today through day $days
		&file_op; #save weather to $file
		my $count=0;
		my $day=(split "t", $what)[0]; #how many days are we looking for
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high=~/\d+/ && $low=~/\d+/ && ++$count<=$day){print "$high$degree/$low$degree$spaces";}
			elsif($count>=$day){print "\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]dt$/ {
		&file_op; #save weather to $file
		my $count1 = my $count2=0;
		my $day=(split "dt", $what)[0]; #how many days are we looking for
		my $flag=1; #print days once
		while(<FILE>){
			#get the high temp
			(my $high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			(my $low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if(/<th>(\b.+\b)<\/th>/ && ++$count1<=$day){ #look for the conditions upto specified day
				$days[$count1-1]=$1; #save day
				&day_space($days);
			}
			elsif($high=~/\d+/ && $low=~/\d+/ && ++$count2<=$day){$ttext.=$high.$degree."/".$low.$degree.$spaces;}
			elsif($count1>=$day && $count2>=$day){print "$dtext\n$lines$ttext\n"; exit;} #don't keep lopking if everything has been found
		}
	}
	case /[1-7]w$/ { #display the weather forecast in words from today through day $days
		&file_op; #save weather to $file
		my $num=(split "w", $what)[0]; #how many are we looking for
		my $count=0; #initialize count
		while(<FILE>){ #cycle through file
			#get the weather
			(my $when) = /<li><strong>(\b.+\b\:)<\/strong>/;
			(my $weather) = /<\/strong>(.+)<\/li>/;
			$weather=$when.$weather;
			#print weather
			if($when && ++$count<=$num){
				#print "$when";
				print wrap($initial_tab, $subsequent_tab, $weather);
				print "\n";
			}
			elsif($count>=$num){exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]p$/ { #if conditions of specified day
		&file_op; #save weather to $file
		my $day=(split "p", $what)[0]; #what day are we looking for
		my $flag=0; #set flag for when we find start of conditions
		my $count=0; 
		while(<FILE>){
			if(/^<tr class="titles">\s*$/){$flag=1;} #found the start of conditions
			elsif($flag && /(\b.+\b)<\/td>/ && ++$count==$day){ #look for the conditions for specified day
				$cnd=$1; #save conditions
				&cond_symb ($cnd); #translate conditions to symbol
			}
			elsif($count>=$day){print "$ctext\n"; exit;} #don't keep looking if everything has been found
		}
	}
	case /[1-5]$/ { #if temp of specified day 
		&file_op; #save weather to $file
		while(<FILE>){
			#get the high temp
			($high) = /<td><strong>High: (-?\d+)&deg;<\/strong><span>Low: \-?\d+&deg;<\/span><\/td>/;
			#get the low temp
			($low) = /<td><strong>High: \-?\d+&deg;<\/strong><span>Low: (-?\d+)&deg;<\/span><\/td>/;
			#print the high and low temp for the specified day
			if($high && $low && ++$count==$what){print "$high$degree/$low$degree\n";}
		}
	}
	else { #didn't give proper options
		&usage; #print usage error
	}
}

#print "\n"; # need endline to make things look nice

close FILE;

sub file_op { #do file operations
	if(-e $file ){ #does the file exist and is not empty?
		my $size=`stat -c %s $file`;
		if($size >= 1000){
			my $date=`date -u +%s`; #get current date in seconds
			my $created=`stat -c %Y $file`; #get creation date of file in seconds
			$age=$date - $created; #determine age of file
		}
		else{
			$age=$update+1;
		}
	}
	else{ #if file doesn't exist make it and set to update the file
		`touch $file`;
		$age=$update+1;
	}

	if ($age>=$update){ #only get a new file every hour
		#obtain the weather forecast and store it in $file
		`wget -O - http://weather.yahoo.com/forecast/"$code"_"$system".html > $file`;
	}
	open(FILE, $file) or die "Could not open file $file: $!\n";
}

sub usage { #if correct options haven't been passed usage error
		print "Usage error weather.pl <citycode> <system> <option>\n";
		print "weather.pl <citycode> <system> <option>\n";
		print "\t<citycode> - weather.com city code\n";
		print "\t<system> - c for metric or f for imperial\n";
		print "\t<option> - Only one option can be entered at a time\n";
		print "\t\tc displays current conditions\n";
		print "\t\tw displays list of current conditions\n";
		print "\t\tcp displays current conditions symbol\n";
		print "\t\tt displays current temp in chosen system\n";
		print "\t\t[1-5]d displays the days up to specified day\n"; 
		print "\t\t[1-5]dp displays condition symbol for days up to specified day\n";
		print "\t\t[1-5]t displays high/low temp in chosen system up to specified day\n";
		print "\t\t[1-5]dt displays high/low temp in chosen system and then days up to specified day\n";
		print "\t\t[1-7]w displays the weather in words up number specified\n";
		print "\t\t[1-5]p displays conditions for specified day\n";
		print "\t\t[1-5] displays high/low temp in chosen system for specified day\n";
}

sub cond_symb { #translates conditions into symbol in weather font
	if ($_ =~ "Partly Cloudy"){$_="c";}
	elsif ($_ =~ "Fair" || $_ =~ "Sun" || $_ =~ "Clear"){$_="A";}
	elsif ($_ =~ "Cloud"){$_="e";}
	elsif ($_ =~ "Storm" || $_ =~ "Thunder" || $_ =~ "T-"){$_="i";}
	elsif ($_ =~ "Snow" || $_ =~ "Flurries" || $_ =~ "Wintry"){$_="k";}
	elsif ($_ =~ "Rain"){$_="h";}
	elsif ($_ =~ "Shower"){$_="g";}
	$ctext.=$_.$fspaces;
}

sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Hoy      ";}
	elsif ($_ =~ "Tonight"){$_="  Noc      ";}
	elsif ($_ =~ "Tomorrow"){$_="Mañ";}
	elsif ($_ =~ "Thu"){$_="      Jue";}
	elsif ($_ =~ "Fri"){$_="      Vie";}
	elsif ($_ =~ "Sat"){$_="      Sab";}
	elsif ($_ =~ "Sun"){$_="      Dom";}
	elsif ($_ =~ "Mon"){$_="      Lun";}
	elsif ($_ =~ "Tue"){$_="      Mar";}
	elsif ($_ =~ "Wed"){$_="      Mié";}
	$dtext.=$_.$dspaces;
}

```
Have a nice day folks.
Bruce

---

### Post by arrakis31 on 2008-02-28
Sorry newbie question:

What is the weather.html file ???? from the script weather.pl

*****************************************

$file="/tmp/weather.html"; #temp holding weather

*****************************************

I don't get that, can someone please give more detail
Thanks !!!!!

---

### Post by lvleph on 2008-02-28
It is just where the information is saved so that the script can then print it up. It is just a temporary file. If you were to open the file you would see the gmail atom.

---

### Post by Cammy on 2008-02-29
> **Bruce M. said:**
> It been a while since I've made any changes to my conky, other then tweaking text alignment in the weather.  What was 3 conkys at one time have been reduced to one.

Wow, and to think there was a time where I figured your conky would eventually grow to consume your entire desktop and you'd have to add a second monitor to accommodate it.  :lolflag:

---

### Post by Bruce M. on 2008-02-29
> **Cammy said:**
> Wow, and to think there was a time where I figured your conky would eventually grow to consume your entire desktop and you'd have to add a second monitor to accommodate it.  :lolflag:

Granted there is a lot of stuff there that really isn't needed, it was a learning process just getting it there.  But now that it's there it's kinda stuck on me.

Multitasking in Gusty is an "iffy" thing, because I have such an old CPU that frequently gets up to 90%-100% and the system locks up until the CPU usage drops.

For example opening FF with nothing else happening pushes the CPU usage as high as 62%

Seriously thinking in Xbuntu 7.10 or going back to Feisty..  :(

---

### Post by Cammy on 2008-02-29
Yeah Bruce, you've got an old machine there.  I'm fortunate in that I can wait a bit longer before upgrading hardware.  Do you know if it's possible to upgrade your bios and install a faster cpu on your board?

---

### Post by Bruce M. on 2008-02-29
> **Cammy said:**
> Yeah Bruce, you've got an old machine there.  I'm fortunate in that I can wait a bit longer before upgrading hardware.  Do you know if it's possible to upgrade your bios and install a faster cpu on your board?

Have no idea about the BIOS, but the CPU can be upgraded to something like 900 - 920MHtz, not really worth the $$$$.  :(

---

### Post by Cammy on 2008-02-29
> **Bruce M. said:**
> Have no idea about the BIOS, but the CPU can be upgraded to something like 900 - 920MHtz, not really worth the $$$$.  :(

Ahh, I mentioned the bios because my board's original limit was something like a 2700+, but doing a flash bios upgrade allowed it to take the 3200+ chip.  And by the time I bought the chip, the price had come way down because the next great thing was already out.  I think my 3200+ cpu was something like $45.

---

### Post by Linuturk on 2008-03-05
Thanks for this! I was looking for this kind of weather script.

[[IMG]http://img509.imageshack.us/img509/3050/03052008shotrk5.th.png[/IMG]](http://img509.imageshack.us/my.php?image=03052008shotrk5.png)

---

### Post by aonegodman on 2008-03-06
> **Bruce M. said:**
> It been a while since I've made any changes to my conky, other then tweaking text alignment in the weather.  What was 3 conkys at one time have been reduced to one.

So here's my "finished" conky:

Have a nice day folks.
Bruce

Hey there partner, been a while for me too.  :)

"BM_Conky"  looks good.  Hope all is well on the home front down there. What's your next project?

:lol:

John

---

### Post by lvleph on 2008-03-06
> **Linuturk said:**
> Thanks for this! I was looking for this kind of weather script.

[[IMG]http://img509.imageshack.us/img509/3050/03052008shotrk5.th.png[/IMG]](http://img509.imageshack.us/my.php?image=03052008shotrk5.png)

That is so weird. I would have sworn you lived next door to me. Your forecast is almost exactly the same as mine but we live over 1000 miles apart. Are you sure you changed the city code?

---

### Post by SomeGuyDude on 2008-03-06
I'm very perplexed. I followed the directions (skipped the font step), chmod'd the file, and my conkyrc is attached, but quite literally nothing shows up. My conky just gets a little space up top. No weather.

```
own_window_hints undecorated,below,skip_taskbar
background no
double_buffer yes
use_spacer yes
use_xft yes
update_interval 2.5
minimum_size 200 5
maximum_width 200
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders no
uppercase no
border_margin 4
border_width 1
default_color gray
default_shade_color black
default_outline_color white
own_window_transparent yes
alignment top_left
gap_x 20
gap_y 230
override_utf8_locale no
xftfont Trebuchet MS:size=10
#xftalpha 0.8
# ${execi 60 cal -3 | cut -c23-64}


# unused text
# ${color}sda1: ${color}${fs_used} Free / ${fs_size} Total
# ${color}Time: ${color white}${time %k:%M:%S}${alignr}${color}Uptime: ${color white}${uptime}


TEXT
${execi 3600 perl ~/scripts/weather.pl USVA0652 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl USVA0652 f t}
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USVA0652 f cp}$font
${font :size=18}${color white}${alignc}${time %I:%M %p}$color$font
${font :size=11}${color}${alignc}${time %A, %b %d %Y}$color$font
${color}${stippled_hr}
${color white}${alignc}${exec whoami} @ ${nodename}
${color white}${alignc}${execi 1000 cat /etc/lsb-release | grep -i "description" | sed -e 's/DISTRIB_DESCRIPTION=//'}
${color white}${alignc}${sysname} ${kernel} on ${machine}
${color}${stippled_hr}
${color}Connected to: ${color white}${alignr}${wireless_essid eth1}
${color}IP Address:${alignr}${color white}${addr eth1}
${color}Up: ${color white}${upspeed eth1}k/s ${alignr}${color}Down: ${color white}${downspeed eth1}k/s
${color}${stippled_hr}
${color}Uptime: ${color white}$alignr${uptime}
${color}Temp: $alignr${color white}${acpitemp}C
${color}Battery:${color white}${alignr}${battery_percent}%
${color}${stippled_hr}
${color}Processor: $alignr${color white}Intel Core 2 Duo T52
${color}Real-time clock speed: ${color white}$alignr${freq_dyn}Mhz
${color}CPU:${color white} ${cpu}% ${cpubar}
${color}RAM:${color white} ${memperc}% ${membar}

${color}${alignr} MEM%   CPU%
${color}${top_mem name 1}${color white}${alignr}${top_mem mem 1}   ${top_mem cpu 1}
${color}${top_mem name 2}${color white}${alignr}${top_mem mem 2}   ${top_mem cpu 2}
${color}${top_mem name 3}${color white}${alignr}${top_mem mem 3}   ${top_mem cpu 3}
${color}${stippled_hr}
${color}Disk space: ${color white}${fs_used} / ${fs_size}
${color}Used: ${color white}${fs_used_perc /}% ${fs_bar /}
${color}swap: ${color white}${swapperc}% ${swapbar}

```

NOTE: I just put the same lines in from the example to see if something would show up. I'm aware I didn't change the city code or reformat it in any way.

---

### Post by lvleph on 2008-03-06
Change the offsets. Those depend on your screen resolution.

Also, in terminal do the following and make sure you get an output.
```
perl ~/scripts/weather.pl USVA0652 f 5t
```

---

### Post by Bruce M. on 2008-03-07
@ lvleph

Just a question.

For handling the spacing between:
[LIST=1]
[*]weather fonts
[*]day names
[*]hi/lows
[/LIST]
would it be possible to use "bits" rather than a "space"

ie:

[LIST=1]
[*]$sbits="100"; #spacing between each high low.
[*]$fbits="45"; #spacing between condition symbols.
[*]$dbits="83"; #spacing between day names.
[*]$lbits="200"; #each \n represents one line between the days and temps
[/LIST]

Like I said just a thought here and I added the lines thing too.  :)

Have a nice day
Bruce

---

### Post by lvleph on 2008-03-07
I would have to look into how to do that. I am sure there is probably a way, but it may take some digging.

---

### Post by Bruce M. on 2008-03-07
> **lvleph said:**
> I would have to look into how to do that. I am sure there is probably a way, but it may take some digging.

OK, just a thought anyway.

---

### Post by canistra on 2008-03-08
How to make this script to show in metric celsius

---

### Post by lvleph on 2008-03-08
weather <citycode> **c** <option>

---

### Post by holydhaliwal on 2008-03-10
Hey i am trying to get this script to work, the only problem im having is changing it to the metric system as well as getting the right city code to work...i live in montreal so the code is CAXX0301 according the weather.com, however when ever i replace my city code with the default in the script, it doesn't change... infact i've tried with numerous city codes but it always displays the same temp:s any ideas? thanks in advance.

Paul

EDIT: oh btw i also tried "perl ~/scripts/weather.pl USVA0652 f 5t" in the terminal with different city codes and systems, same problem, always the same temp. thanks again

---

### Post by lvleph on 2008-03-11
The city code is suppose to go in the comman call. ie
```
perl ~/scripts/weather.pl CAXX0301 c 5t
```
That command call will give you 5 days of temps in celsius for Montréal.

---

### Post by holydhaliwal on 2008-03-11
Hmm that's strange, now its giving me the weather for montreal...however if i try again in the same session with another city code it stays at montreal, perhaps it doesn't change unless you restart the session or something. or perhaps it has something to do with that html thing thats written by the script every whenever, i dont really know but it works now so thanks!
Oh btw does anyone know what attribute i would assign a window, be it conky or stalonetray for example, so that compiz doesn't draw it a shadow? thanks
EDIT: Oh here's a screeny, i like a minimalistic desktop with as much real estate as possible.
[http://img507.imageshack.us/my.php?image=screenshotxt8.png](http://img507.imageshack.us/my.php?image=screenshotxt8.png)

---

### Post by lvleph on 2008-03-12
It only updates the temporary file every hour. This way it doesn't over load your network by downloading the same information every time you call the script.

I really like your set up. What is the stuff on the right hand side (calendar and the music)?

---

### Post by holydhaliwal on 2008-03-12
The calendar is  called v-call, its on gnome-look in the adesklets and the now playing is screenlets

---

### Post by aonegodman on 2008-03-22
> **holydhaliwal said:**
> The calendar is  called v-call, its on gnome-look in the adesklets and the now playing is screenlets

Really like that desktop. Cool!  :lol:

---

### Post by Bruce M. on 2008-03-22
> **aonegodman said:**
> Really like that desktop. Cool!  :lol:

Hey buddy, you're back.  Where have you been hiding?

---

### Post by Bruce M. on 2008-03-31
What's happened?  Have people stopped visiting this thread?

I see in the other [conky thread]("http://ubuntuforums.org/showthread.php?t=281865") that people are using Conky Weather Revisited but not posting here.

Anyway enough of that I'm here because I finally fixed a problem.

It seemed like every day or two I was "adjusting" the spacings for *day names* and *hi/lows*. They just wouldn't stay in line. Well this morning it hit me :idea: ***Mono fonts*** :idea:, **"i"** is a lot narrower than an **"o"** and **"W"** is wider then other letters.  ***_DUH!_***

so I added mono fonts before the line that calls up day names and hi/lows:
```
${font mono:size=8}${color yellow}${execi 3600 perl ~/scripts/w-days.pl ARBA0009 c 5dt}$color$font
```
BTW, the weather font is set at size=30, and and then I played with the spacing in the **.pl** file:
Near the top:
```
$leadspace=" "; #spacing before each high low
$trailspace=""; #spacing after each high low.
$fspaces=" "; #spacing between condition symbols.
$dspaces=""; #spacing between each day
$lines="\n\n\n"; #each \n represents one line between the days and temps
```
at the bottom:
```
sub day_space { #Adds spaces for aligment
	if ($_ =~ "Today"){$_="  Hoy";}
	elsif ($_ =~ "Tonight"){$_="  Noc";}
	elsif ($_ =~ "Tomorrow"){$_="     Mañ ";}
	elsif ($_ =~ "Thu"){$_="     Jue";}
	elsif ($_ =~ "Fri"){$_="     Vie";}
	elsif ($_ =~ "Sat"){$_="     Sab";}
	elsif ($_ =~ "Sun"){$_="     Dom";}
	elsif ($_ =~ "Mon"){$_="     Lun";}
	elsif ($_ =~ "Tue"){$_="     Mar";}
	elsif ($_ =~ "Wed"){$_="     Mié";}
	$dtext.=$_.$dspaces;
}
```
Of course mine is in Spanish, but it will work for English as well. I also saw where someone is using "Tom" (where my Mañ is) for the display for Tomorrow, which makes sense if you are using the 3 characters (Mon, Tue, Wed, etc.) for the rest of the days.

Anyway, here's the results and will post an EDIT after a few days to let you know if it keeps it's spacing.

The "Ubuntu: Linux for human beings" at the top is a font called: [openlogos]("http://www.dafont.com/openlogos.font") (set at 100 for me).

Have a GREAT day
Bruce

**EDIT:** Five days later and I haven't needed to tweak a thing. So, yes, mono fonts is the answer.

---

### Post by Cammy on 2008-04-01
> **Bruce M. said:**
> Anyway enough of that I'm here because I finally fixed a problem.

I think you invented that problem as an excuse to revive your favorite thread. :lolflag:

---

### Post by lvleph on 2008-04-01
So just to let everyone know, I will most likely not actively develop this anymore, since I do not have an Ubuntu/Linux box to do it on. But I will try to address any issues if they are simple. Basically, what I am saying is that the script won't be changed very much except bug fixes.

---

### Post by Cammy on 2008-04-01
> **lvleph said:**
> So just to let everyone know, I will most likely not actively develop this anymore, since I do not have an Ubuntu/Linux box to do it on. But I will try to address any issues if they are simple. Basically, what I am saying is that the script won't be changed very much except bug fixes.

Thanks for all the work you've done on it!

---

### Post by SanskritFritz on 2008-04-01
> **lvleph said:**
>  I do not have an Ubuntu/Linux box to do it on. But I will try to address any issues if they are simple.Just out of curiosity, may I ask, what have you switched to?

---

### Post by Bruce M. on 2008-04-01
> **lvleph said:**
> So just to let everyone know, I will most likely not actively develop this anymore, since I do not have an Ubuntu/Linux box to do it on. But I will try to address any issues if they are simple. Basically, what I am saying is that the script won't be changed very much except bug fixes.

You did all this **without** Ubuntu!  WoW!

You are using Linux though aren't you?

My hat goes of to you lvleph for doing a great job with this.
It works as advertised.

**Thank you** for your work on Weather Revisited and Weather Revisited 2
Bruce

---

### Post by Bruce M. on 2008-04-01
> **Cammy said:**
> I think you invented that problem as an excuse to revive your favorite thread. :lolflag:

**You just HAD to tell everyone didn't you!**

grumble grumble grumble :lolflag:

Actually, you're wrong ... and right.

It was a real problem, going in and fixing the spacing as the days changed.

I notice today though that they are in perfect alignment just like yesterday.

Yesterday I had: Hoy . Mañ . Mie . Jue . Vie

Today I have: Hoy . Mañ . Jue . Vie . Sab - and the alignment is the same as yesterday.

Colour me happy :)
Bruce

---

### Post by lvleph on 2008-04-03
I wrote it using Ubuntu, but I no longer have an Linux Box, so... Perl scripts are cross platform generally, except this one. However, I do have cygwin and I have install wget, so I can check small erorrs, but I cannot do anything with Conky.

---

### Post by herbertm on 2008-04-04
> **holydhaliwal said:**
> The calendar is  called v-call, its on gnome-look in the adesklets and the now playing is screenlets

Do you have an link or other references to the calendar desklet. I couldn't find it at gnome-look nor elswhere :confused:

Thank You!
 

herbert

---

### Post by Bruce M. on 2008-04-06
Hi Folks,

From my [post #376]("http://ubuntuforums.org/showpost.php?p=4625201&postcount=376") fived days ago. (Then: 1 April - Today: 6 April 08 )

> **Bruce M. said:**
> It seemed like every day or two I was "adjusting" the spacings for *day names* and *hi/lows*. They just wouldn't stay in line. Well this morning it hit me :idea: ***Mono fonts*** :idea:, **"i"** is a lot narrower than an **"o"** and **"W"** is wider then other letters.  ***_DUH!_***


Where I also said:
> Anyway, here's the results and will post an EDIT after a few days to let you know if it keeps it's spacing.

Five days later and I haven't needed to tweak a thing. So, yes, mono fonts is the answer.  :)

Have a GREAT day
Bruce

---

### Post by Kiri on 2008-04-07
My conky was working perfect with the weather script, and now after I removed the weather entries from my conkyrc, conky seems to exit itself after loading after a few seconds. 
Its really strange. I only removed the weather part from the conkyrc
Here it is:

```
# UBUNTU-CONKY
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_xft yes
xftfont Bitstream Vera Sans Mono:size=7
uppercase no
override_utf8_locale yes
use_spacer none

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
# minimum_size 250 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_margin 9

maximum_width 280
minimum_size 280

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color grey

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 960
gap_y 40

# stuff after 'TEXT' will be formatted on screen

TEXT
$color
${color white}$alignc ${exec whoami} @ $nodename ... up for $uptime
${color white}$alignc $sysname $kernel on $machine
${color orange}CPU ${hr 2}$color
${cpu cpu0}% - ${freq}MHz  Load: ${loadavg}  $alignr +${acpitemp}°C
${cpugraph 000000 ffffff}
NVidia v${exec nvidia-settings -q NvidiaDriverVersion | grep Attribute | cut -d ' ' -f 6}$alignr GPU Temp: +${exec nvidia-settings -q GPUCoreTemp | grep Attribute | cut -d ' ' -f 6 | cut -c 1-2}°C

${color #ffcb48}Processes ${hr 2}
  ${color #98c2c7}NAME             PID       CPU%      MEM%
  ${color #e5e5e5}${top name 1} ${top pid 1}   ${top cpu 1}    ${top mem 1}
  ${color #e5e5e5}${top name 2} ${top pid 2}   ${top cpu 2}    ${top mem 2}
  ${color #e5e5e5}${top name 3} ${top pid 3}   ${top cpu 3}    ${top mem 3}
  ${color #e5e5e5}${top name 4} ${top pid 4}   ${top cpu 4}    ${top mem 4}

${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}
${color lightgrey} ${top_mem name 4}${top_mem mem 4}

${color orange}MEMORY / DISK ${hr 2}$color
RAM:   $memperc%   ${membar 6}$color
Swap:  $swapperc%   ${swapbar 6}$color

${color orange}FILE SYSTEM ${hr 2}$color
root:  ${fs_used_perc /}%  ${fs_bar 6,120 /}  ${fs_free /} free $color
home:  ${fs_used_perc /home}%  ${fs_bar 6,120 /home}  ${fs_free /home} free $color
data:  ${fs_used_perc /media/sda9}%  ${fs_bar 6,120 /media/sda9}  ${fs_free /media/sda9} free $color
ipod:  ${fs_used_perc /media/IPOD OF KI}%  ${fs_bar 6,120 /media/IPOD OF KI}  ${fs_free /media/IPOD OF KI} free $color

${color orange}NETWORK (${addr wlan0}) ${hr 2}$color
Down: $color${downspeed wlan0} k/s ${alignr}Up: ${upspeed wlan0} k/s
${downspeedgraph wlan0 25,140 000000 ff0000} ${alignr}${upspeedgraph wlan0
25,140 000000 00ff00}$color
Total: ${totaldown wlan0} ${alignr}Total: ${totalup wlan0}
Inbound: ${tcp_portmon 1 32767 count} Outbound: ${tcp_portmon 32768
61000 count}${alignr}Total: ${tcp_portmon 1 65535 count}

${color orange}LOGGING ${hr 2}$color
${execi 30 tail -n3 /var/log/messages | fold -w50}
```


Any ideas what might be wrong?

---

### Post by andahunter on 2008-04-07
hello there i like the all how its written but dont kno what it means, its something about forecast and u can download a plugin for firefox 2 check ure weather :D nice of seeing u

---

### Post by Bruce M. on 2008-04-07
> **Kiri said:**
> My conky was working perfect with the weather script, and now after I removed the weather entries from my conkyrc, conky seems to exit itself after loading after a few seconds. 
Its really strange. I only removed the weather part from the conkyrc

Any ideas what might be wrong?

How do you start your conky?

Terminal, or autostart with a script?

Is a script please show us.

Mine is like this:

```
#!/bin/bash
sleep 30 &&
conky -c ~/.conkyscripts/conkymain &
```

---

### Post by Kiri on 2008-04-07
Both actually. Its supposed to load on startup, and was doing so before. But now does not. And if I type nohup conky in terminal, it starts, but then exits after a few seconds for no apparent reason. It doesn't even output an error or anything.

It was working fine before I put the weather stuff in. And was working fine WITH the weather stuff in. Now that Ive removed the weather stuff, it doesnt work. Really weird. I dont get it.

---

### Post by Frak on 2008-04-07
Weird. It worked fine the first time I used it, screwed something up, replaced the files with the EXACT SAME, and now it gives me multiple compilation errors.

---

### Post by SomeGuyDude on 2008-04-08
Not sure if this has been mentioned, but for some reason in Hardy my temp display is gone. I have the weather icon, the conditions, but can't show the temperature.

---

### Post by Kiri on 2008-04-08
Well I can't seem to fix conky now no matter what. Ive tried re-installing it, several different conkyrc 's, even with nothing but one line of text it still crashes. 
Have no idea whats going on. Some how removing the weather part really messed it uo :( I want my conky back

---

### Post by Bruce M. on 2008-04-08
As of today my weather isn't working, conky is, just no weather.
Turned my machine on this AM and nothing.
Puzzling to say the least.

---

### Post by dccrens on 2008-04-08
The issue is that that it looks like yahoo has changed their xml format. They also put a disclaimer saying it is their data... I don't know enough xml and perl to puzzle out hot to get it fixed but it is easy to see that the file DL'ed by the wget is changed.

---

### Post by Doorslammer on 2008-04-08
mine stopped working as well 
still have the current condions  but not the 5 day forcast

---

### Post by Cammy on 2008-04-08
Same here. :(  And with lvleph not working on it anymore, the prognosis doesn't look good.

---

### Post by yns73 on 2008-04-09
5 days forecast stopped working also on my conky. current conditions work for the moment.

---

### Post by jjgomera on 2008-04-09
same here :(

---

### Post by SomeGuyDude on 2008-04-09
Damn. This was one of my favorite aspects of conky...

However, conditions works fine. I have my little cloud icon and "light rain", but no temperature.

---

### Post by lvleph on 2008-04-09
I look into it. It may be a simple fix.

---

### Post by lvleph on 2008-04-09
I read the license agreement. So I would have to find a different site to grab info from. I am afraid Conky Weather Revisited is officially defunct, until someone comes up with an alternate way of getting the data. It would need to be world wide weather.

Their license does say to use [http://www.nws.noaa.gov/](http://www.nws.noaa.gov/). That was at least nice of them. lol The issue is that is not international.

---

### Post by ZonedOut on 2008-04-09
I developed a script in Python since I don't know any Perl.  It uses the RSS feed from Yahoo! weather for its information.  I basically set it up the same way lvleph did it so you should be able to keep your conkyrc file mostly the same.  Copy this script into a file called "weather.py":
```

#! /usr/bin/python

import urllib
import sys
from xml.dom import minidom

class weather:
    def __init__(self, zip_code, units):
        WEATHER_URL = 'http://xml.weather.yahoo.com/forecastrss?p=%s&u=%s'
        WEATHER_NS = 'http://xml.weather.yahoo.com/ns/rss/1.0'
        url = WEATHER_URL % (zip_code, units)
        dom = minidom.parse(urllib.urlopen(url))
        self.forecasts = []
        for node in dom.getElementsByTagNameNS(WEATHER_NS, 'forecast'):
            self.forecasts.append({
                'day': node.getAttribute('day'),
                'low': node.getAttribute('low'),
                'high': node.getAttribute('high'),
                'condition': node.getAttribute('text')
            })
        self.ycondition = dom.getElementsByTagNameNS(WEATHER_NS, 'condition')[0]
        self.ywind = dom.getElementsByTagNameNS(WEATHER_NS, 'wind')[0]
        self.yunits = dom.getElementsByTagNameNS(WEATHER_NS, 'units')[0]
        self.yatmos = dom.getElementsByTagNameNS(WEATHER_NS, 'atmosphere')[0]

        self.temp_unit = self.yunits.getAttribute('temperature')
        self.speed_unit = self.yunits.getAttribute('speed')

        self.current_condition = self.ycondition.getAttribute('text')
        self.current_temp = self.ycondition.getAttribute('temp')
        self.current_wind = self.ywind.getAttribute('speed')
        self.current_humidity = self.yatmos.getAttribute('humidity')
 
    def print_current_temp(self):
        return self.current_temp + ' ' + self.temp_unit
    def print_current_wind(self):
        return self.current_wind + ' ' + self.speed_unit
    def print_current_humidity(self):
        return self.current_humidity + '%'
    def print_symbol(self, condition):
        if condition == "Partly Cloudy" or \
           condition == "Mostly Cloudy":
            return 'c'
        elif condition == "Fair" or \
             condition == "Sun" or \
             condition == "Clear":
            return 'A'
        elif condition == "Cloud" or \
             condition == "Fog":
            return 'e'
        elif condition == "Storm" or \
             condition == "Thunder" or \
             condition == "T-":
            return 'i'
        elif condition == "Snow" or \
             condition == "Flurries" or \
             condition == "Wintry":
            return 'k'
        elif condition == "Rain" or \
             condition == "Drizzle":
            return 'h'
        elif condition == "Showers":
            return 'g'
    def print_forecast_conditions(self):
        for cond in self.forecasts:
            print cond['day'] + ': ' + cond['condition'] + ' ' + \
                  'High: ' + cond['high'] + self.temp_unit + ' Low: '\
                  + cond['low'] + self.temp_unit
    def print_forecast_symbols(self):
        for cond in self.forecasts:
            print self.print_symbol(cond['condition']),
        print '\n'
    def print_forecast_temps(self):
        for cond in self.forecasts:
            print cond['high'] + self.temp_unit + '/' + cond['low'] + self.temp_unit + '\t',
        print '\n'
    def print_forecast_days(self):
        for cond in self.forecasts:
            print cond['day'] + '\t\t',
        print '\n'
                              
if __name__== "__main__":
    yweather = weather(sys.argv[1], sys.argv[2])
    if sys.argv[3] == 'c':
        print yweather.current_condition
    if sys.argv[3] == 'w':
        # Current conditions
        print "Temperature: " + yweather.print_current_temp()
        print "Wind: " + yweather.print_current_wind()
        print "Humidity: " +yweather.print_current_humidity()
    if sys.argv[3] == 't':
        # Temp
        print yweather.print_current_temp()
    if sys.argv[3] == 'cp':
        # Current Symbol
        print yweather.print_symbol(yweather.current_condition)
    if sys.argv[3] == 'dn':
        # Forecast Days
        yweather.print_forecast_days()
    if sys.argv[3] == 'dp':
        # Forecast Symbols
        yweather.print_forecast_symbols()
    if sys.argv[3] == 'd':
        # Forecast Conditions
        yweather.print_forecast_conditions()
    if sys.argv[3] == 'dt':
        # Forecast Temps
        yweather.print_forecast_temps()


```

Make it executable:
```
chmod +x weather.py
```

Then go into your conkyrc file and change all of the "perl" to "python" and "weather.pl" to "weather.py".  Also, the RSS only has a 2 day forecast so I just made a "dp" command rather than "[1-5]dp".  So, remove the numbers from the commands.  It could look something like this:

```
${color lightgrey}$hr
${voffset -3}$alignc CURRENT CONDITIONS
${voffset -7}$hr $color
${execi 3600 python ~/weather.py 46037 f w}
${voffset -30}$alignr${offset -50}${execi 3600 python ~/weather.py 46037 f t}
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 python ~/weather.py 46037 f cp}$font
${voffset -10}${color lightgrey}$hr
${voffset -3}$alignc FORECAST
${voffset -7}$hr $color
${font weather:size=45}${execi 3600 python ~/weather.py 46037 f dp}${font}$color
${voffset -55}${execi 3600 python ~/weather.py 46037 f dt}
${execi 3600 python ~/weather.py 46037 f d}
```

Hopefully, someone can improve upon this but it's a start and the above conky output is similar to the original but with only a 2 day forecast and no weather messages for each day.  I think it should have a longer lifetime since the RSS tags probably won't change like the HTML that was used in the original.

---

### Post by SomeGuyDude on 2008-04-09
It's a start, but it doesn't work QUITE right. The following:

```
TEXT
  ${font weather:size=45}${execi 3600 python ~/scripts/weather.py USPA1290 f cp}${font}
${color white}${execi 3600 python ~/scripts/weather.py USPA1290 f t} ${execi 3600 python ~/scripts/weather.py USPA1290 f c}
${color}Email: ${color white}${execi 300 python ~/scripts/gmail.py}
${color}$mpd_status ${color white}$alignr$mpd_elapsed/$mpd_length
$mpd_smart
```

Yields the following. As you can see, the conditions "image" is muffed a bit, and I've totally lost my "current conditions" part. For the time being, I'm using both scripts, since part of the old one still works.

---

### Post by ZonedOut on 2008-04-09
Sorry, totally missed the "c" command since I wasn't using it.  I edited my previous post to include the code for the "c" command.  I believe it just printed out the current condition?  Hope that fixes it up.

---

### Post by ZonedOut on 2008-04-10
I figured out why your image was messed up because it happened to me this morning.  It's because some of the conditions don't match what's in my script.  I'll take a look this evening to see if I can't make it more robust.

---

### Post by lvleph on 2008-04-10
The thing with using anything from Yahoo now is that their license agreement does not allow you to do that. I would fix my script to work, but then I would be violating the license agreement, which means I cannot post that here.

---

### Post by dccrens on 2008-04-10
For those of use in the States the NOAA info looks interesting. I might have to start learning perl...

---

### Post by lvleph on 2008-04-10
It doesn't have to be written in Perl. I used Perl, because of the power of Regular Expressions. Other languages can use Regular Expressions, but Perl and RegEx go hand in hand. Also, I don't like python.

---

### Post by lvleph on 2008-04-10
Okay, I was reading over the license agree again. I actually think there is no reason, why I can't just grab their data. If I can't grab their data, then neither should any webbrowser. I suppose I should say something about Yahoo, just to be on the safe side. When I get time I will look into what needs to be corrected.

---

### Post by Bruce M. on 2008-04-10
Something I don't understand here, and I'm not a programmer so please excuse my ignorance on the subject.

I have been using the "original" way to get weather ( with the **.sh** file) in conjuction with CWR (Conky Weather Revisited) from the beginning.

My weather.sh file uses: [http://xoap.weather.com/](http://xoap.weather.com/) as the site to grab the information, and CWR uses: [http://weather.yahoo.com/](http://weather.yahoo.com/) as a starting point, then when I go to Buenos Aires on both sites they end up at exactly the same place: [Buenos Aires]("http://www.weather.com/outlook/travel/businesstraveler/local/ARBA0009?from=search_city").

However my weather.sh file is still working perfectly, and CWR did download the file to /tmp/weather.html this morning.

Since the weather.html file is there, and the coding in the page hasn't changed, how come CWR can't read it?

Could it be that the *weather.sh* file doesn't "save" the page there by creating a load on the server?

Just some questions / thoughts.
Have a nice day
Bruce

---

### Post by lvleph on 2008-04-10
The shell script doesn't use regular expressions, and instead knows where things are. In theory the regular expression should be a little less sensitive to changes than a position lookup. However, the way I did some of the regular expressions ended up being more sensitive to change than I hoped. The fix for the code is actually not hard, I just don't have the time right now. I have my own programs to write for research, so those come first. If someone know RegEx, it would be easy to fix. The code itself does not need to change much, it is just the RegEx.

---

### Post by SomeGuyDude on 2008-04-10
Works again for me! Thanks Zoned!

Now if I could just make it spit out a degree symbol again... I've been hammering away at it but to no avail so far.

---

### Post by ZonedOut on 2008-04-10
I guess since lvleph is going to continue to support his script, I shouldn't hijack his thread.  I thought he was abandoning it, so I thought I would make an alternative.  The RSS feed is limited so you'll be able to get more information out of his script anyway once it's fixed.

---

### Post by Frak on 2008-04-11
> **SomeGuyDude said:**
> Works again for me! Thanks Zoned!

Now if I could just make it spit out a degree symbol again... I've been hammering away at it but to no avail so far.
At the beginning of your conkyrc script, where it says

```
override_utf8_locale no
```

Change that to

```
override_utf8_locale yes
```

---

### Post by lvleph on 2008-04-12
If you want to take over development that is fine with me. But it would be more useful to everyone here if you made a new thread, so that you can update the first post. I really don't have a lot of time to develop this so... In the start I was hoping that I would get some help, but that never happened.

---

### Post by kaivalagi on 2008-04-12
I started a new thread 3 days ago for an alternative python based script for weather data. The solution is currently based on PyMetar and as such only gives current weather details.

The thread is here:[ http://ubuntuforums.org/showthread.php?t=750532]("http://ubuntuforums.org/showthread.php?t=750532"). There are full instructions on it's setup there.

I am about to start knocking together a newer version which will provide forecasting details too, it will be based on weather.com's xml feed. The AWN weather applet uses this and so I will be taking some of the python script work that's gone into that.

Cheers

---

### Post by Bruce M. on 2008-04-12
> **lvleph said:**
> If you want to take over development that is fine with me. But it would be more useful to everyone here if you made a new thread, so that you can update the first post. I really don't have a lot of time to develop this so... In the start I was hoping that I would get some help, but that never happened.

Good Luck with what ever the future brings you.
***Thank you*** for your work here.

BRuce

---

### Post by yousillygoose on 2008-04-12
Hello hello.

Thank you so much for your contribution. I loved the forecasting weather.  I only know a small amount of java being the only language i know.  I most definitely would like to see this project continued.  i relied more on the forecasting weather then the current weather (as current weather is kinda obvious).  

I was wondering if anyone wanted to attempt to revise this script (if lvleph would allow it) or even write our own script.  I would take the time to learn some of the language but a team up on this would work well.  Any takers?

---

### Post by wnelson on 2008-04-13
Why is it that on some days multiday forcast you get the correct characters and temps and on other days it is just blank?

---

### Post by Bruce M. on 2008-04-13
> **yousillygoose said:**
> Hello hello.

Thank you so much for your contribution. I loved the forecasting weather.  I only know a small amount of java being the only language i know.  I most definitely would like to see this project continued.  i relied more on the forecasting weather then the current weather (as current weather is kinda obvious).  

I was wondering if anyone wanted to attempt to revise this script (if lvleph would allow it) or even write our own script.  I would take the time to learn some of the language but a team up on this would work well.  Any takers?

> **wnelson said:**
> Why is it that on some days multiday forcast you get the correct characters and temps and on other days it is just blank?

Hi yousillygoose y wnelson

If you look at post #416 there is an alternative. It's using python not perl but it is there.

I to would love to see this perl script grabbed by a programmer and maybe use [Weather Underground]("http://www.wunderground.com/") as it's source. The [Terms of Service]("http://www.wunderground.com/members/tos.asp") there are very favourable for this type of stuff for "members" which is free (although the $10/year option is selected by default). The idea of getting a 5 day forecast with only two execi calls is really a good one.

So until someone grabs this perl script and starts supporting it the only option available is kaivalagi's python script: [Conky Weather Python Scripts Based On Metar / Weather.com XOAP service]("http://ubuntuforums.org/showthread.php?t=750532").

**Any Perl writers available?**

I'm still thankful to lvleph for what he started.
Have a great day
Bruce

---

### Post by yousillygoose on 2008-04-13
> **Bruce M. said:**
> Hi yousillygoose y wnelson

If you look at post #416 there is an alternative. It's using python not perl but it is there.

I to would love to see this perl script grabbed by a programmer and maybe use [Weather Underground]("http://www.wunderground.com/") as it's source. The [Terms of Service]("http://www.wunderground.com/members/tos.asp") there are very favourable for this type of stuff for "members" which is free (although the $10/year option is selected by default). The idea of getting a 5 day forecast with only two execi calls is really a good one.

So until someone grabs this perl script and starts supporting it the only option available is kaivalagi's python script: [Conky Weather Python Scripts Based On Metar / Weather.com XOAP service]("http://ubuntuforums.org/showthread.php?t=750532").

**Any Perl writers available?**

I'm still thankful to lvleph for what he started.
Have a great day
Bruce


Doesnt this script only pull in current weather or forecasting weather only by many exec's?  Wouldn't that be fairly slow and energy needing??

---

### Post by billybag on 2008-04-20
can someone help me with my conky script. i cant seem to get anything to appear under weather.

```

# UBUNTU-CONKY
# A comprehensive conky script, configured for use on
# Ubuntu / Debian Gnome, without the need for any external scripts.
#
# Based on conky-jc and the default .conkyrc.
# INCLUDES:
# - tail of /var/log/messages 
# - netstat connections to your computer
#
# -- Pengo (conky@pengo.us)
#

# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
background no

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer yes
use_xft yes

# Update interval in seconds
update_interval 3.0

# Minimum size of text area
minimum_size 400 5

# Draw shades?
draw_shades no

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no

uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 1

# border margins
border_margin 1

# border width
border_width 1

# Default colors and also border colors, grey90 == #e5e5e5
default_color white
default_shade_color black
default_outline_color grey90

own_window_colour brown
own_window_transparent yes

# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x -245
gap_y 3

# stuff after 'TEXT' will be formatted on screen

override_utf8_locale yes
xftfont Terminus:size=7
xftalpha 0.8

# Coisas para rever mais tarde

#${offset 240}${color}${font weather:size=26}y ${font}FSB ${i2c tempf 1} °F
#${offset 240}${color slate grey}Temperature:
#${offset 240}${color}${font weather:size=26}z ${font}CPU ${i2c tempf 2} °F

TEXT
${color slate grey}${time %a, } ${color }${time %I:%M %P}
${color slate grey}${time %Z,    }${color }${time %H:%M:%S}

${voffset -1}${color}${font OpenLogos:size=30}    u
${voffset -25}${color}${font StyleBats:size=12}O ${font}${color slate grey}UpTime: ${color }$uptime
${color}${font StyleBats:size=12}Q ${font}${color slate grey}Kern:${color }$kernel
${color}${font StyleBats:size=12}A ${font}${color slate grey}CPU:${color } $cpu% ${acpitempf}F
${cpugraph 20,140 000000 ffffff}
${color slate grey}Load: ${color }$loadavg
${color slate grey}Processes: ${color }$processes  
${color slate grey}Running:   ${color }$running_processes

${color}${font Webdings:size=12}i ${font}${color slate grey}Highest CPU:
${color #ddaa00} ${top name 1}${top cpu 1}
${color lightgrey} ${top name 2}${top cpu 2}
${color lightgrey} ${top name 3}${top cpu 3}

${color}${font Webdings:size=12}i ${font}${color slate grey}Highest MEM:
${color #ddaa00} ${top_mem name 1}${top_mem mem 1}
${color lightgrey} ${top_mem name 2}${top_mem mem 2}
${color lightgrey} ${top_mem name 3}${top_mem mem 3}

${color slate grey}MEM:  ${color } $memperc% $mem/$memmax
${membar 3,140}
${color slate grey}SWAP: ${color } $swapperc% $swap/$swapmax
${swapbar 3,140}

${color slate grey}ROOT:    ${color }${fs_free /}/${fs_size /}
${fs_bar 3,140 /}
${color slate grey}HOME:  ${color }${fs_free /home}/${fs_size /home}
${fs_bar 3,140 /home}

${color slate grey}Internet:
${color}${font PizzaDude Bullets:size=12}M${font}  Tot.up. ${totalup eth0} Kb/s
${voffset 1}${color}${font PizzaDude Bullets:size=12}v${font}  Up: ${color }${upspeed eth0}k/s
${upspeedgraph eth0 20,140 000000 ffffff}
${voffset 6}${color}${font PizzaDude Bullets:size=12}S${font}  Tot.dow. ${totaldown eth0} Kb/s
${voffset 1}${color}${font PizzaDude Bullets:size=12}r${font}  Down: ${color }${downspeed eth0}k/s
${downspeedgraph eth0 20,140 000000 ffffff}

${voffset -14}${color}${font Martin Vogel's Symbols:size=16}B${font}${color slate grey}Mail:
${color }You have ${color3}${texeci 60 perl ~/scripts/gmail.pl n} ${color}new mail(s)

${color slate grey}Weather:
${color}${execi 3600 perl ~/scripts/weather.pl USMA0195 f 3d}
${color}${font weather:size=47}${execi 3600 perl ~/scripts/weather.pl USMA0195 f 3dp}${font}
${color}${execi 3600 perl ~/scripts/weather.pl USMA0195 f 3t}
${voffset 5}${color}${font MusiSync:size=17}G${font}${color slate grey} MusicPlayer:

```

i have tried using some of the generic weather conky scripts that people posted on here and they work fine. so i know that at least my weather.pl script is correct and my above script did work at one point but randomly stopped after i replaced gutsy with linux mint (which is based on gutsy currently)

---

### Post by lvleph on 2008-04-20
Yahoo has changed things and so the script no longer works. I don't have time to maintain the code, so someone else developed their own. There should be a link a few posts back.

---

### Post by Bruce M. on 2008-04-21
There is a new python script at:

[Conky Weather Python Script]("http://ubuntuforums.org/showthread.php?t=760527")

---

### Post by cm690 on 2008-04-23
Too late to find out v2 version of weather script. I just modified v1 version of weather script to work with Yahoo changes.

---

### Post by Frak on 2008-04-23
> **cm690 said:**
> Too late to find out v2 version of weather script. I just modified v1 version of weather script to work with Yahoo changes.
OK, once more for those that didn't hear it. **Yahoo! no longer allows this!**
People are now using another python script for another service. Should be about 1 or 2 pages back.

---

### Post by dccrens on 2008-05-06
Wel everything has been working very well until today. I started recieving errors that say:
Unexpexted error: < type 'exceptions.IndexError'>
Unable to interrodate the current conditions data

This happens for all of the call I as using, Temp, Precip, etc.

Anyone else having this problem?

If I run one of the calls from the command line I get:

python ~/Scripts/conkyForecast.py --location=USVA0427 -i --refetch --datatype=LT

Unexpected error:  <type 'exceptions.IndexError'>
Unable to interrogate the current conditions data
Unexpected error:  <type 'exceptions.IndexError'>
Unable to interrogate the forecast data
Traceback (most recent call last):
  File "/home/dccrens/Scripts/conkyForecast.py", line 855, in <module>
    weather.output_data()
  File "/home/dccrens/Scripts/conkyForecast.py", line 646, in output_data
    string = self.current_conditions[0].low
IndexError: list index out of range

---

### Post by jjgomera on 2008-05-07
maybe you must change to this other weather script, its a active project:

 :arrow:  [Conky Weather Python Script]("http://ubuntuforums.org/showthread.php?t=760527")

---

### Post by Frak on 2008-05-07
> **jjgomera said:**
> maybe you must change to this other weather script, its a active project:

 :arrow:  [Conky Weather Python Script]("http://ubuntuforums.org/showthread.php?t=760527")
This was already discussed 1 or 2 pages back.

---

### Post by jjgomera on 2008-05-08
> **Frak said:**
> This was already discussed 1 or 2 pages back.
yeah, and now i think he use that, but i think he must post it in the other thread ;)

---

### Post by bangladesh on 2008-05-26
> **Bruce M. said:**
> Something I don't understand here, and I'm not a programmer so please excuse my ignorance on the subject.

I have been using the "original" way to get weather ( with the **.sh** file) in conjuction with CWR (Conky Weather Revisited) from the beginning.

My weather.sh file uses: [http://xoap.weather.com/](http://xoap.weather.com/) as the site to grab the information, and CWR uses: [http://weather.yahoo.com/](http://weather.yahoo.com/) as a starting point, then when I go to Buenos Aires on both sites they end up at exactly the same place: [Buenos Aires]("http://www.weather.com/outlook/travel/businesstraveler/local/ARBA0009?from=search_city").

However my weather.sh file is still working perfectly, and CWR did download the file to /tmp/weather.html this morning.

Since the weather.html file is there, and the coding in the page hasn't changed, how come CWR can't read it?

Could it be that the *weather.sh* file doesn't "save" the page there by creating a load on the server?

Just some questions / thoughts.
Have a nice day
Bruce

Hi Bruce, ¿would you mind to share your conkyrc with me? the one that made that screenshot you posted.
When i get home i'll try to make it work, but a conkyrc from baires would simplify me understanding things (i just discover this conky stuff).
Gracias.

---

### Post by bangladesh on 2008-05-28
HEy there. I've doing a little (very little) research to find out how does it work. I'm trying tod translate the output of the conkyweather that bruce posted in here

[http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489](http://ubuntuforums.org/showpost.php?p=4157750&postcount=1489)

But i only could transalte the xslt texts that the script prints directly (i don't know how to explain myself, so i'll put the weather.xslt so you can see what i meen) to spanish.
The other thing i didn't figured out how-to-do-it is the icons of the weather to show on my conky. I installed the font (weather.ttf i think) just like lvleph explained at the begining, but until now i didn't make it work.

here is "my" weather.xslt (ofcourse, i didn't wrote this, just translated the <xsl:text> contents </xsl:text> )
```

<!-- 

 This XSLT is used to translate an XML response from the weather.com
 XML API. 

 You can format this file to your liking. Two things you may feel 
 like doing:

	1) Modify the layout of the fields or static text already defined
	2) Add other fields from the XML response file that aren't referenced in this
	   XSLT. You can grab a full list by just doing a: 
           wget "http://xoap.weather.com/weather/local/$LOCID?cc=*&unit=$UNITS" 
           (change $LOCID and $UNITS to suit your needs)
-->

<xsl:stylesheet xmlns:xsl="http://www.w3.org/1999/XSL/Transform" version="1.0" > 
	<xsl:output method="text" disable-output-escaping="yes"/>
	<xsl:template match="weather">
			<xsl:apply-templates select="loc"/>
			<xsl:apply-templates select="cc"/>
			<xsl:apply-templates select="dayf/day[@d='1']"/>
	</xsl:template>
	
			<xsl:template match="loc">

<xsl:text>Desde:  </xsl:text><xsl:value-of select="dnam"/>
<xsl:text>
Lat: </xsl:text><xsl:value-of select="lat"/>
<xsl:text>                  Long: </xsl:text><xsl:value-of select="lon"/>
<xsl:text>
Sol: Salida: </xsl:text><xsl:value-of select="sunr"/>
<xsl:text>  Puesta: </xsl:text><xsl:value-of select="suns"/>

			</xsl:template>

			<xsl:template match="cc">#

<xsl:text>

Temp: </xsl:text><xsl:value-of select="tmp"/><xsl:value-of select="/weather/head/ut"/>

<xsl:text>      Sensación térmica: </xsl:text><xsl:value-of select="flik"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text>

Condiciones: </xsl:text><xsl:value-of select="t"/>
<xsl:text>
Visibilidad: </xsl:text><xsl:value-of select="vis"/><xsl:text> KM</xsl:text>
<xsl:text>      Humedad: </xsl:text><xsl:value-of select="hmid"/><xsl:text>%</xsl:text>
<xsl:text>
Viento: </xsl:text>
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>0</xsl:text></xsl:when>
	<xsl:otherwise><xsl:value-of select="wind/s"/></xsl:otherwise>
</xsl:choose>
<xsl:value-of select="/weather/head/us"/> 
<xsl:choose>
	<xsl:when test="wind/s = 'calm'"><xsl:text>(0 km/h)</xsl:text></xsl:when>
	<xsl:otherwise><xsl:text> (</xsl:text><xsl:value-of select="round(wind/s * 0.6214)"/><xsl:text> mph)</xsl:text></xsl:otherwise>
</xsl:choose>
<xsl:text> (</xsl:text><xsl:value-of select="wind/t"/>
<xsl:text>)</xsl:text>

<xsl:text>
Presión atmosférica: </xsl:text><xsl:value-of select="bar/r"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="bar/d"/>

<xsl:text>
Indice UV: </xsl:text><xsl:value-of select="uv/i"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="uv/t"/>
<xsl:text>         Punto de rocío: </xsl:text><xsl:value-of select="dewp"/>

<xsl:text>

Luna: Icon: </xsl:text><xsl:value-of select="moon/icon"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="moon/t"/>

	</xsl:template>

	<xsl:template match="dayf/day[@d='1']">
<xsl:text>
Mañana: </xsl:text><xsl:value-of select="low"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> a </xsl:text><xsl:value-of select="hi"/><xsl:value-of select="/weather/head/ut"/>
<xsl:text> ~ </xsl:text><xsl:value-of select="part[@p='d']/t"/>
<xsl:text>
  </xsl:text><xsl:value-of select="/weather/swa/a/t"/>
<xsl:text>
</xsl:text>
	</xsl:template>

</xsl:stylesheet>
```

Is there anyway to grab the things that i couldn't translate? I'm trying to make it entirely spanish.
I think i only have to translate this kind of things: 
<xsl:value-of select="part[@p='d']/t"/>

¿any clues?

Thanks very much. I attach my conkyweather just in case


EDIT: I found that the python proyect already has traductions. Thank's anyway.

---

### Post by PatrickMoore on 2008-06-07
do i have to create a new script or do i enter the info to my conkyrc file?

```
background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.6
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

${execi 3600 perl ~/scripts/weather.pl USIL0360 f 1w}
${execi 3600 perl ~/scripts/weather.pl USIL0360 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl 72584 f t}
${voffset -15}$alignr${offset -60}${font weather:size=32}${execi 3600 perl ~/scripts/weather.pl 72584 f cp}$font
5 DAY FORECAST ${hr 1}${color}

${font weather:size=55}${execi 3600 perl ~/scripts/weather.pl 72584 f 5dp}${font}$color
${voffset -70}${execi 3600 perl ~/scripts/weather.pl USIL0360 f 5dt}

```

the weather report is in my conky display im a tad confused.. heres a screenshot if it helps too.

---

### Post by steve101101 on 2008-06-15
I just put the weather into my configuration, but the 5 day forecast isn't working. whats wrong? thanks.

---

### Post by steve101101 on 2008-06-15
this is my configuiration file ...

```

# weather stuff

update_interval 1.0

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
xftfont Candera:size=6
uppercase no
override_utf8_locale yes
use_spacer no
#weather stuff end


# set to yes if you want Conky to be forked in the background
background no

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
gap_y 70
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

TEXT

${color #0077ff}$sysname $kernel 
${color #0077ff}$machine - $nodename 

Intel(R) Core(TM)2 Quad CPU Q6600 @ 2.4 GHz

$Core 1: $#0077ff${freq 1} MHz $alignc${color #0077ff}${cpubar 5, 120 cpu1}$#0077ff ${cpu cpu1}%
${color #0077ff}Core 2: $#0077ff${freq 2} MHz $alignc${color #0077ff}${cpubar 5, 120 cpu2}$#0077ff ${cpu cpu2}%
${color #0077ff}Core 3: $#0077ff${freq 3} MHz $alignc${color #0077ff}${cpubar 5, 120 cpu3}$#0077ff ${cpu cpu3}%
${color #0077ff}Core 4: $#0077ff${freq 4} MHz $alignc${color #0077ff}${cpubar 5, 120 cpu4}$#0077ff ${cpu cpu4}%

${color #0077ff}RAM:        4 GB ${color #0077ff}${membar 5,120} ${memperc}%

${color #0077ff}Hard Disks: - Free Space $fs_free_perc%

${color #0077ff}${rss http://rss.news.yahoo.com/rss/topstories 60 item_titles 10}

${color1}$hr
${voffset -3}$alignc CURRENT CONDITIONS 
${voffset -7}$hr $color
${execi 3600 perl ~/scripts/weather.pl USVA0652 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl USVA0652 f t}
${voffset -15}$alignr${offset -60}${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USVA0652 f cp}$font
${voffset -10}${color1}$hr
${voffset -3}$alignc 5 DAY FORECAST 
${voffset -7}$hr $color
${font weather:size=45}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5dp}${font}$color
${voffset -55}${execi 3600 perl ~/scripts/weather.pl USVA0652 f 5dt}
${execi 3600 perl ~/scripts/weather.pl USVA0652 f 7w}

```

---

### Post by PatrickMoore on 2008-06-25
```
background yes
font Zekton:size=8
xftfont Zekton:size=8
use_xft yes
xftalpha 0.1
update_interval 0.6
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
default_color 000000
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

Home: ${alignr}${fs_free /home} / ${fs_size /home}
${fs_bar 4 /}
Storage: ${alignr}${fs_free /media/disk} / ${fs_size /media/disk}
${fs_bar 4 /media/disk}

NETWORK ${hr 1}${color}

Down ${downspeed wlan0} k/s ${alignr}Up ${upspeed wlan0} k/s
${downspeedgraph wlan0 24,128} ${alignr}${upspeedgraph wlan0 24,128}
Total ${totaldown wlan0} ${alignr}Total ${totalup wlan0}

CURRENT CONDITIONS ${hr 1}${color}

${execi 3600 perl ~/scripts/weather.pl 60123 f 1w}
${execi 3600 perl ~/scripts/weather.pl 60123 f w}
${voffset -30}$alignr${offset -50}${execi 3600 perl ~/scripts/weather.pl 60123 f t}
${voffset -15}$alignr${offset -60}${font weather:size=32}${execi 3600 perl ~/scripts/weather.pl 60123 f cp}$font
5 DAY FORECAST ${hr 1}${color}

${font weather:size=55}${execi 3600 perl ~/scripts/weather.pl 60123 f 5dp}${font}$color
${voffset -70}${execi 3600 perl ~/scripts/weather.pl 60123 f 5dt}

```

im having a hard time trying to configure the weather am i missing a plugin? i have python my zipcode is correct i dont know but i do need help

---

### Post by lvleph on 2008-06-25
Last I knew my weather script was no longer working, because of changes in the yahoo weather site I was getting the info from.

---

### Post by kaivalagi on 2008-06-25
An alternative python script which uses weather.com to source the data instead can be found here: -> [http://ubuntuforums.org/showthread.php?t=760527](http://ubuntuforums.org/showthread.php?t=760527)

---


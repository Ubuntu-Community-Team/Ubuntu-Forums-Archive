---
title: "RRD Yearly graph only shows 5 months, HDD temp"
date: 2009-01-25
forum: General Help
---

### Post by Per Olav on 2009-01-25
My rrd perl thingy has been running for quite som time now, but the yearly graph only shows the last 5 months, then nothing. I guess there's a mistake in this perl script somewhere, but can't find it.

```

#!/usr/bin/perl
use RRDs;

# define location of rrdtool databases
my $rrd = '/var/lib/rrd';
# define location of images
my $img = '/var/www/mainframe/rrdtool';

# process data for each specified HDD (add/delete as required)
&ProcessHDD("hda", "160GB Western Digital Raid1");
#&ProcessHDD("hdb", "primary slave");
&ProcessHDD("hdc", "160GB Western Digital Raid1");
#&ProcessHDD("hdd", "secondary slave");
&ProcessSensors("0", "1"); 

sub ProcessHDD
{
# process HDD
# inputs: $_[0]: hdd (ie, hda, etc)
#         $_[1]: hdd description

	# get hdd temp for master drive on secondary IDE channel
	my $temp=`/usr/sbin/hddtemp -n /dev/$_[0]`;
	# remove eol chars and white space
	$temp =~ s/[\n ]//g;
	
	print "$_[1] (/dev/$_[0]) temp: $temp degrees C\n";

	# if rrdtool database doesn't exist, create it
	if (! -e "$rrd/$_[0].rrd")
	{
		print "creating rrd database for /dev/$_[0]...\n";
		RRDs::create "$rrd/$_[0].rrd",
			"-s 60",
			"DS:temp:GAUGE:600:0:100",
			"RRA:AVERAGE:0.5:1:576",
			"RRA:AVERAGE:0.5:6:672",
			"RRA:AVERAGE:0.5:24:732",
			"RRA:AVERAGE:0.5:144:1460";
	}

	# insert value into rrd
	RRDs::update "$rrd/$_[0].rrd",
		"-t", "temp",
		"N:$temp";
}
sub ProcessSensors
{
# process HDD
# inputs: $_[0]: hdd (ie, hda, etc)
#         $_[1]: hdd description

	# get hdd temp for master drive on secondary IDE channel
	my $temp1=`/usr/bin/sensors | grep M/B|cut -b 15-16`;
	# remove eol chars and white space
	$temp1 =~ s/[\n ]//g;

         print "M/B temp: $temp1 degrees C\n";
                                       
        # if rrdtool database doesn't exist, create it
        if (! -e "$rrd/sensors.rrd")
        {
		print "creating rrd database for temperature info";
                RRDs::create "$rrd/sensors.rrd",
                      "-s 60",
                      "DS:temp:GAUGE:600:0:100",
                      "RRA:AVERAGE:0.5:1:576",
                      "RRA:AVERAGE:0.5:6:672",
                      "RRA:AVERAGE:0.5:24:732",
                      "RRA:AVERAGE:0.5:144:1460";
         }
           # insert value into rrd
           RRDs::update "$rrd/sensors.rrd",
	                 "-t", "temp",
                         "N:$temp1";
}              
                                                                                      

	# create graphs
	&CreateGraph($_[0], "day", $_[1]);
	&CreateGraph($_[0], "week", $_[1]);
	&CreateGraph($_[0], "month", $_[1]);
	&CreateGraph($_[0], "year", $_[1]);


sub CreateGraph
{
# creates graph
# inputs: $_[0]: hdd name (ie, hda, etc)
#         $_[1]: interval (ie, day, week, month, year)
#         $_[2]: hdd description

	RRDs::graph "$img/hddtemp-$_[1].png",
		"--lazy",
		"-s -1$_[1]",
		"-t hdd temperature :: mainframe raid array",
		"-h", "80", "-w", "600",
		"-a", "PNG",
		"-v degrees C",
		"--slope-mode",
		"DEF:hda=$rrd/hda.rrd:temp:AVERAGE",
                "DEF:hdc=$rrd/hdc.rrd:temp:AVERAGE",
                "DEF:mb=$rrd/sensors.rrd:temp:AVERAGE",
                     "LINE2:hda#FF9900:160GB Western Digital         ",
                     "GPRINT:hda:MIN:  Min\\: %2.lf",
                     "GPRINT:hda:MAX: Max\\: %2.lf",
                     "GPRINT:hda:AVERAGE: Avg\\: %4.1lf",
                     "GPRINT:hda:LAST: Current\\: %2.lf degrees C\\n",
                     "LINE2:hdc#CC00CC:160GB Western Digital         ",
                     "GPRINT:hdc:MIN:  Min\\: %2.lf",
                     "GPRINT:hdc:MAX: Max\\: %2.lf",
                     "GPRINT:hdc:AVERAGE: Avg\\: %4.1lf",
                     "GPRINT:hdc:LAST: Current\\: %2.lf degrees C\\n",
                     "LINE2:mb#EE0000:Motherboard                   ",
                     "GPRINT:mb:MIN:  Min\\: %2.lf",
                     "GPRINT:mb:MAX: Max\\: %2.lf",
                     "GPRINT:mb:AVERAGE: Avg\\: %4.1lf",
                     "GPRINT:mb:LAST: Current\\: %2.lf degrees C\\n";
                                                                                                                          

	if ($ERROR = RRDs::error) { print "$0: unable to generate $_[0] graph: $ERROR\n"; }
}

```

---


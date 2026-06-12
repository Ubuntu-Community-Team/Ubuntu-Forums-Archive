---
title: "How to feed ffmpeg a list of files as input/output"
date: 2008-12-27
forum: General Help
---

### Post by jerome1232 on 2008-12-27
I'm wanting to feed a list of .flv videos into ffmpeg and convert them to .avi's. That's my specific example but this is more for general use. (I have alot of video files to convert of various types)

I'm wondering how do you feed ffmpeg a list of files like that? So can I search a directory for all .flv's (using say find) then feed the absolute paths it comes up with one at a time to ffmpeg for conversion then remove the orginal file?

Can you truncate the extension so that you can feed the same file name and append a new extension as the output name?

---

### Post by mc4man on 2008-12-27
This may be of no value and is only an example of a batch command for ffmpeg that converts all .aaa to .bbb, keeping the file name with new extension

In this case I have it as a nautilus script that converts all the .flac in a dir.to .mp3 with same file name. In my case I then cp the .mp3's to a new dir. and remove the.mp3's from the conversion dir.

Maybe you can do something using the the structure of the conversion command.

The command before making script

```
for f in *.flac; do ffmpeg -i "$f" -acodec mp3 -ab 256k "${f%.flac}.mp3"; done &&  cp  --copy-contents *.mp3 ~/Music/portable && rm -R *.mp3


```

---

### Post by jerome1232 on 2008-12-27
That's perfect actually, I had no idea. 

I don't understand why the for loop is grabbing file names from the current directory but it's certainly working. I think I need to get myself a bash programming book or something. :)

Thanks.

---

### Post by Dr Small on 2008-12-27
> **jerome1232 said:**
> That's perfect actually, I had no idea. 

I don't understand why the for loop is grabbing file names from the current directory but it's certainly working. I think I need to get myself a bash programming book or something. :)

Thanks.
I was going to suggest the for loop myself.

This part:
```
for f in *.flac
```

Is listing all files in the current directory that match the wildcard of *.flac. No other files that match this criteria will be included. For example, only using * would include all files in this for loop.

So now, we are saying, for each file that matches *.flv, do this.
We assigned the current filename to the variable f, so in order to to do any converting with ffmpeg, we use the variable $f in place of the actual filename.

I hope that explains the for loop in the process a little bit :)

---

### Post by romeyde on 2009-01-10
This may help.   Here's a quick and dirty script I wrote recently to take tv shows recorded by my tuner and covert them to mp4 for playing on the ps3, via mediatomb.   It runs once a day at 3am via cron.  Still needs a bit of tweaking but works well as is for me.

```

#!/usr/bin/perl
my $inputdir = "/data/media/recordings";
my $outputdir = "/media/MyBook/media/PCTV";

my @filenames = glob("$inputdir/*.m2t");
exit 0 if (!@filenames);

foreach $filename (@filenames) {
	next if (-M "$filename" < 0.05); ### skip if less than 1 hour old
	$filename =~ m/.+recordings\/(.+)-(\d{8})-.+/;
	$basename = $1; $date = $2;
	if (!$date) { ### one off recording, lets just move it
		$filename =~ m/.+recordings\/(.+)/;
		my $newfilename = $1;
		print "Moving: $filename\n";
		`/bin/mv $filename $outputdir/${newfilename}`;
		next;
	}
	print "Converting: $filename\n";
	my $newfilename = "${outputdir}/${basename}/${basename}-${date}.mp4";
	if (!-e "$outputdir/$basename") {
		`/bin/mkdir $outputdir/$basename`;
	}
	else {
		### already been converted?
		next if (-e "$newfilename");
	}
	my $start = time;
	`/usr/bin/ffmpeg -i $filename -y -vcodec libx264 -acodec libfaac -f mp4 -mbd rd -flags 4mv+trell+aic+qprd+mv0 -coder 0 -me_method epzs -subq 0 -sc_threshold -1 -cmp 2 -subcmp 2 -flags2 dct8x8+skiprd -level 41 -bf 3 -ac 2 -ab 128 -threads 3 -s hd720 ${inputdir}/${basename}-${date}.mp4`;
	my $end = time;
	my $totaltime = $end - $start;
	if ($totaltime < 900) {  ### went to fast, failed?
		print "\twarning: ffmpeg only took $totaltime seconds\n";
		# delete failed attempt
		unlink("${inputdir}/${basename}-${date}.mp4") if (-e "${inputdir}/${basename}-${date}.mp4");
		# keep the original I guess
		print "\t/bin/mv $filename ${outputdir}/${basename}/${basename}-${date}.m2t\n";
		`/bin/mv $filename ${outputdir}/${basename}/${basename}-${date}.m2t`;
		next;
	}
	else {
		print "\t/bin/mv ${inputdir}/${basename}-${date}.mp4 ${outputdir}/${basename}/.\n";
		`/bin/mv ${inputdir}/${basename}-${date}.mp4 ${outputdir}/${basename}/.`;
		if (-e "$newfilename") { ### move worked
			unlink("$filename"); ### rm the original
		}
		my $minutes = sprintf "%0.2f", ($totaltime/60);
		print "\tconverted file in $minutes minutes\n";
	}
}

```

---


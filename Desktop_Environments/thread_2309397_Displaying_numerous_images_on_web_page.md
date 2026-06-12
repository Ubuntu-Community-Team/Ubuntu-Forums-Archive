---
title: "Displaying numerous images on web page"
date: 2016-01-10
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-01-10
Folks,

Not sure if this should me under networking or media section but hope someone may be able to suggest an option.

I run a small web server, I know how to display images within a web page but would like to have a directory containing numerous images available to view. I don't want to list them individually with links but would like friends to view them and save if required.

Is there any way an image browser can be used on a web directory?

Geffers

---

### Post by SeijiSensei on 2016-01-10
There are some open-source gallery applications like [Gallery2]("http://galleryproject.org/").  In my case I just wrote a simple script to create a [tabular gallery](http://www.takinganimeseriously.com/images/) in PHP:

```

	<html>
	<body>
	
	<h3>Image Gallery</h3>
		
<?php
# where the images reside; including trailing slash
$imgdir="/path/to/the/images/directory/";

# displayed thumbnail width
$max_width=150;

# images per row
$per_row=4;

# No user-serviceable parts below

$files=explode("\n",`ls $imgdir | egrep 'gif|png|jpg|jpeg'`);
$rows=ceil(count($files)/$per_row);
$avcounter=0;
?>
	<h4>There are <?=count($files)?> images available.</h4>

	<p>Click on an image to make it full-size.</p>	
	<p>Right-click an image and choose "Save" to download it.</p>

	<table>
	
<?php
for ($r=0; $r<$rows; $r++) {
	
	$sizerow="";
	echo "<tr>";
	
	for ($c=0; $c<$per_row; $c++) {
	    
	    if (!empty($files[$avcounter])) {
		$fn=$imgdir.$files[$avcounter];
		$imgdata=getimagesize($fn);
		$width=$imgdata[0];
		$height=$imgdata[1];
		
		$sizerow.="<td style=\"font-family: Arial, Helvetica, sans-serif;
			  font-size: 12px; font-weight:bold; padding-left:12px; padding-right:12px\">".
		  $files[$avcounter]."<br/>($width x $height) ";
		
		$fs=filesize($imgdir.$files[$avcounter]);
		if ($fs < 2048) {
		    $sizerow.=number_format($fs)."B";
		} else {
		    $sizerow.=number_format($fs/1024)."K";
		}
		
		if ($width>$max_width) {		    
		    $scale=$max_width/$imgdata[0];
		    $width=floor($width*$scale);
		    $height=floor($height*$scale);
		}		 
		$imgsize="width=$width height=$height";
		
		echo "<td style=\"padding:12px\">";
		echo "<a href=\"/images/".$files[$avcounter]."\">";
		echo "<img $imgsize src=\"/images/".$files[$avcounter]."\"></a></td>";
	    
	    }
	    
	    $avcounter++;
	    if ($avcounter>count($files)) {
		echo "</tr>\n";
		break;
	    } 
	    
	}
    
    echo "</tr>\n";
    echo "<tr>$sizerow</tr>\n";
}
?>
	</table>
	</body>
	</html>

```

---

### Post by Geoff_Lane on 2016-01-11
Thank you [URL="http://ubuntuforums.org/member.php?u=698195"][B][COLOR=#000000]SeijiSensei

geffers

[/COLOR][/B][/URL]

---

### Post by SeijiSensei on 2016-01-11
Glad I could help. I take it you're just using the script?

I did notice one thing that might not work for you out-of-the-box.

```

		echo "<td style=\"padding:12px\">";
		echo "<a href=\"/images/".$files[$avcounter]."\">";
		echo "<img $imgsize src=\"/images/".$files[$avcounter]."\"></a></td>";

```

Those lines assume the images can be accessed by the URI "/images/filename".  If that doesn't work for you, change "/images/" to the appropriate directory name.

---

### Post by Geoff_Lane on 2016-01-11
Haven't tried it yet, saved the script.

Nothing to do with this thread but my main Ubuntu laptop suffered a failure recently so hopping between a 9" netbook and my Raspberry Pi running Mate :)

Geffers

---


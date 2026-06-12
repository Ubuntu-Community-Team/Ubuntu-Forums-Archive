---
title: "Need a command-line &quot;site crawler&quot;"
date: 2009-02-15
forum: General Help
---

### Post by camerong on 2009-02-15
hey all.. i have a modest request but I have no idea where to even begin looking...

I need a program that I can supply a URL to and it will crawl the site and return all page URL's with their respective titles. it should not leave the site it is assigned to.

so somethign like

> $ crawl [http://www.somesite.com/](http://www.somesite.com/)
[http://www.somesite.com/home.html](http://www.somesite.com/home.html) | WELCOME TO SOMESITE
[http://www.somesite.com/news.html](http://www.somesite.com/news.html) | SOMESITE NEWS
[http://www.somesite.com/2/3/blahs.html](http://www.somesite.com/2/3/blahs.html) | SOMESITE blah 3 2!

I tried to write this in PHP but I failed pretty badly:
```
<html>
<head><title>PHP Website Crawler</title></head>
<body>
<form id="crawl" method="post" action="">
<label>URL:
<input name="url" type="text" id="url" value="<?php $url; ?>http://website.com" size="70" maxlength="255" />
</label>
<label>
<input type="submit" name="Submit" value="Crawl!" />
</label>
</form>
</body>
</html>
<?php
// $crawled - array of urls crawled
// $tocrawl - array of urls to crawl
// $index - array of all pages + kwds

$crawled = Array();
$tocraw = Array();
$index = Array();

function crawl($url)
{
	global $crawled, $tocrawl, $index, $x;

	$input = @file_get_contents($url) or die('Could not access file: $url');
echo "<pre>".$url."</pre>";
	$regexp = "<a\s[^>]*href=(\"??)([^\" >]*?)\\1[^>]*>(.*)<\/a>";
	if(preg_match_all("/$regexp/siU", $input, $matches))
	{
		echo $matches[2][$x]."<br>";
		if (strpos($matches[2][$x], $url) === false) { } else {
			if (in_array($matches[2][$x], $crawled)) { } else {
				array_push($tocrawl, $matches[2][$x]);
			}
			if (in_array($matches[2][$x], $index)) { } else {
				$index[$x][0] = $matches[2][$x]; //urls
				$index[$x][1] = $matches[3][$x]; //kwds
			}
		}
	}
}

if (isset($_POST['url'])) {

$url = str_replace("www.", "", $_POST['url']);
$tocrawl[0] = $url;
$x = 0;

while ($tocrawl[$x] != null)
{
	crawl($tocrawl[$x]);
	array_push($crawled, $tocrawl[$x]);
	$x++;
}

echo "<pre>";
print_r($crawled);
print_r($tocrawl);
print_r($index);
echo "</pre>";

}
?>
```

All help is appreciated! Thanks in advance. :confused: :(

---

### Post by Old *ix Geek on 2009-02-15
Have you looked at **wget**?  It might need some fiddling to do exactly what you're after, but it may work.

---

### Post by camerong on 2009-02-15
as far as i'm aware, wget will fetch a website.

i would need to use wget recursively, and to only fetch the links of the website which are to the current domain, and i also need the titles...

its a bit more than tweaking.. i was hoping there would be some crawlers already wrriten..

---

### Post by FluffyElmo on 2009-02-15
This is in Ruby not PHP, but looks similar to what you want. I'm not aware of any pre-built tools that do what you want, I think a little bit of programming will be necessary whatever you do.
[http://mikeburnscoder.wordpress.com/2007/03/31/spider-the-web-with-ruby/](http://mikeburnscoder.wordpress.com/2007/03/31/spider-the-web-with-ruby/)

---

### Post by redsoxreed on 2009-02-15
Is lynx what you're looking for?


lynx.isc.org

---


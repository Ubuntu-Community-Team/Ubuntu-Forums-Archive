---
title: "Conky script for monitoring stock prices"
date: 2008-12-21
forum: General Help
---

### Post by HighInBC on 2008-12-21
I made a little script for myself to monitor stocks in conky.

This is hard coded for the way I like it, but it would not be difficult to change. You will need to install the Cache::FileCache module to use this.

You can also install the Finance::Quote module and uncomment the three lines and use the conversion rate for your currency.

This is by no means a finished application, but it is a good starting point for you own customized stock script.

```

#!/usr/bin/perl
use strict;
use LWP::Simple;
use Cache::FileCache;

#use Finance::Quote;
#my $q = Finance::Quote->new;
#my $conversion_rate = $q->currency("USD","CAD");

my %patterns =
(
 'last'                => 'id="ref_\d+_l">([\d\.]+)</span><br>',
 'open'                => 'id="ref_\d+_op">([\d\.]+)</span></td>',
 'high'                => 'id="ref_\d+_hi">([\d\.]+)</span></td>',
 'low'                 => 'id="ref_\d+_lo">([\d\.]+)</span></td>',
 'volume'              => 'id="ref_\d+_vo">([\d\.]+M?)</span></td>',
 'todays_change'       => 'id="ref_\d+_c">([-+]?[\d\.]+)</span></span>',
);
my ( undef, undef, $hour, undef, undef, undef, $wday ) = gmtime();
my ( $market, $symbol, $quantity ) = @ARGV;

my $cache = new Cache::FileCache();
my $cache_time = (( ( $wday > 0 ) && ( $wday < 6 ) && ( $hour < 9 ) ) ? ( '10 seconds' ) : ( '1 hour' ));
my $cache_name = ( ".google_finance-$market-$symbol.cache" );
my $html = $cache->get( $cache_name );
if ( not defined $html )
  {
  $html = get( 'http://finance.google.ca/finance?client=ob&q='.$market.':'.$symbol );
  $cache->set( $cache_name, $html, $cache_time );
  }

my %data;
foreach my $key ( keys( %patterns ) )
  {
  $html =~ m"$patterns{$key}" || next;
  $data{$key} = $1;
  }

my $color = (( $data{'todays_change'} >= 0 ) ? ( 'green' ) : ( 'red' ));
my $value = sprintf("%0.2f", ( $data{'last'} * $quantity ));
my $percent = sprintf("%0.2f%%",(($data{'todays_change'} / $data{'open'}) * 100));

printf (
        '${color white} %-7s%-6s${color %s}%-5s(%s)${color white}%8s%6s%12s'."\n",
        ( $market, $symbol, $color, $data{'todays_change'}, $percent, $data{'last'}, $quantity, $value )
       );

```

This would be called like this in conky:

```

${color}Stock         Change          Last    Quant.  Value
${execpi 10 ~/.conky/google_finance2.pl NASDAQ AMZN 190}

```

It is very easy to add more stocks without a lot of clutter in your config file.

This script will only contact google every hour instead of every 10 seconds when the market is closed. I am not sure if I got the market times right, and I think when daylight savings rolls around it will be off an hour. It is a work in progress.

A table for the open times of the different markets should be made as they are not all the same.

Feel free to post updates, fixes, and improvements.

---

### Post by HighInBC on 2008-12-21
Oh, I have a question. How to I put a dollar sign($) in conky output??

---

### Post by mklebel on 2009-08-27
Illegal division by zero at /home/mitchell/scripts/stocks.pl line 43.

?

---

### Post by mklebel on 2009-08-27
looks like google changed their code, I think your pattern for 'open' isnt' matching.


Nice idea though, I'm going to re-write this in python or php (something that I know) that way I an keep up with google and their changes.

---


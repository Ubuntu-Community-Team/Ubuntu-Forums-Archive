---
title: "Vegas Video Poker Real Life Pay Tester Program"
date: 2009-03-22
forum: Gaming &amp; Leisure
---

### Post by fixitdude on 2009-03-22
Next time you go and play Video Poker at a Casino you can have a edge knowing how different strategies work and how pay table changes effect your pay back.

You can pick the starting bet amount, the number of games played and how many times it reports back.

For example in this version you start with 400 coins, 1 coin per bet, the computer will play 400,000 games for you, and display win totals at every 20,000 games. More games than you will ever play but shows you what might happen if you spent a lifetime as a sick gambler :)

Graphics are not needed, you want SPEED, so this runs in terminal mode.

You can modify this code to change anything you want, it's written in perl and can be edited in KWrite. Most people would probably just want to change the pay tables and the number of games played, but more advanced changes could include changing the strategies for holding cards.

Installing is easy, copy and paste the code from here into KWrite, save it as "poker.pl", open a terminal and "cd" to where it is, "chmod 755 poker.pl" to make it executable, then "perl poker.pl" and away it goes!

Coin in, number of games etc.. is at the first few lines (pretty obvious), the pay table in this version is 1-2-3-4-6-9-25-200-800 you can see it at about line 227, the numbers are in the sections as "$win = (X * $coins_per_bet)" Where "X" is the number for that win type. If you don't understand what I just said you probably don't want to modify this part.

To see exactly what it's doing, try turning on the debug printout.

After a while of changing stuff you start to realize why the casinos always make money. Watch out for casinos that have bad video poker pay tables, that is a good indication that their slots are also set to take your money. It's all about the math.

Some code was picked up on the net in bits and pieces from everywhere then totally modified so it's under GPL. Have fun.

```

#!/usr/bin/perl

$starting_balance = 400;  # number of coins to start with
$coins_per_bet = 1;  # number of coins for each bet
$stop_at_games = 400000;  # max number of games to play
$display_every = 20000;  # display status every x games

$debug = 0;  # set to 1 for debug printout

$balance = $starting_balance;
$last_bal = $balance;
$gamectr = 0;
$displayctr = 0;

$win_royals = 0;  # counters for display
$win_sf = 0;
$win_4ofak = 0;
$win_fullh = 0;
$win_f = 0;
$win_s = 0;
$win_3ofak = 0;
$win_2p = 0;
$win_jb = 0;

srand; # call the randomizer once at start

while (($gamectr < $stop_at_games)){ # && ($balance > 0)){


# basic deck of cards from 2 - A clubs through spades.
@init_suits =  ('C','H','D','S');
@init_nums = (2,3,4,5,6,7,8,9,10,'J','Q','K','A');
$i = 0;

foreach $suit (@init_suits){
  	foreach $num (@init_nums){
    		$init_cards[$i] = "$num.$suit";
    		$i++;
    		}
 	}

#foreach $left_in_deck (@init_cards){
#	print "$left_in_deck \n";
#	}

#print "\n\n";

@new = ();

# @init_cards should have all the cards in it now.
# shuffle the deck
  while (@init_cards){
	push(@new, splice(@init_cards, rand @init_cards, 1));
	}

# @new now has the shuffled cards, so we stick it back into the array
# @init_cards.

  @init_cards = @new;

#foreach $left_in_deck (@init_cards){
#	print "$left_in_deck \n";
#	}

if ($debug) { print "\n"; }

foreach $pos (0,1,2,3,4){
	$card = shift(@init_cards);
 	$jscard = $card;
    $jscard =~ s/\./_/g;
    if ($debug) { print "$card "; }
    $keep[$pos] = $card;
	}


&find_wins(); # find any wins (subroutine)

$leave_alone = 0;  # leave hand alone if we find a winner
$draw_again = 0;

if($straight == 1 && $flush == 1 && $royal == 1){
	$leave_alone = 1;
	}
elsif($straight == 1 && $flush == 1){
	$leave_alone = 2;
	}
elsif($fourofakind){
	$leave_alone = 3;
	}
elsif($threeofakind && $pair == 1){
	$leave_alone = 4;
	}
elsif($flush == 1){
	$leave_alone = 5;
	}
elsif($straight == 1){
	$leave_alone = 6;
	}
elsif($threeofakind){
#	$leave_alone = 7;
	}
elsif($pair == 2){
	$leave_alone = 8;
	}
elsif($jacksorbetter == 1){
	$leave_alone = 9;
	}

foreach $pos (0,1,2,3,4){ # clear keep2
    $keep2[$pos] = "";
	}


if (leave_alone != 1 && leave_alone != 2 &&
    leave_alone != 3 && leave_alone != 4) { # didn't find good stuff, find possible royal
       foreach $pos (0,1,2,3,4){ # go through and keep any high cards
             if($keep[$pos] =~ /10|J|Q|K|A/) {
if ($debug) { print "ROYALxxx=$keep[$pos] "; }
             foreach $pos2 (0,1,2,3,4){ # go through and keep any high cards
                if($pos2 != $pos) {
                   if($keep[$pos2] =~ /10|J|Q|K|A/) {
if ($debug) { print "ROYALxxx1=$keep[$pos2] "; }
                      foreach $pos3 (0,1,2,3,4){ # go through and keep any high cards
                         if($pos3 != $pos && $pos3 != $pos2) {
                            if($keep[$pos3] =~ /10|J|Q|K|A/) {
if ($debug) { print "ROYALxxx2=$keep[$pos3] "; }
                         ($n1,$s1) = split(/\./, $keep[$pos]); # check suits
                         ($n2,$s2) = split(/\./, $keep[$pos2]); # check suits
                         ($n3,$s3) = split(/\./, $keep[$pos3]); # check suits
                         if(($s1 eq $s2) && ($s2 eq $s3)) {
                            $keep2[$pos] = $keep[$pos]; # keep both cards
                            $keep2[$pos2] = $keep[$pos2];
                            $keep2[$pos3] = $keep[$pos3];
                            $draw_again = 1; # indicate we need to draw more cards
                            if ($debug) { print "ROYALkeep=$keep[$pos],$keep[$pos2],$keep[$pos3] "; }
                            $leave_alone = 10; # skip everything else
                            }
                           }
                          }
                          }
                         }
	                  }
                  }
             }
        }
    }


if ($leave_alone == 0) { # no winner so hold good cards

   $kind2_flag = 0;
   foreach $num (@init_nums){
	   if($cards{$num} >= 2){
          foreach $pos (0,1,2,3,4){ # go through and keep them all
             if ($keep[$pos] =~ $num) {
                $keep2[$pos] = $keep[$pos];
                if ($debug) { print "keep=$keep[$pos] num=$num "; }
                $kind2_flag = 1; # indicate we held at least 2 cards
                }
	         }
          }
       }

   if ($kind2_flag == 1) { # didn't find 2 so now hold high cards
          foreach $pos (0,1,2,3,4){ # go through and keep any high cards
             if ($keep[$pos] =~ /J|Q|K|A/) {
                $keep2[$pos] = $keep[$pos];
                if ($debug) { print "J-Akeep=$keep[$pos] "; }
                last;
                }
	         }
         }

   if ($kind2_flag == 0) { # didn't find 2 so now hold high cards
          foreach $pos (0,1,2,3,4){ # go through and keep any high cards
             if ($keep[$pos] =~ /J|Q|K|A/) {
                $keep2[$pos] = $keep[$pos];
                if ($debug) { print "J-Akeep=$keep[$pos] "; }
                }
	         }
         }
   $draw_again = 1; # indicate we need to draw more cards
   }

if($leave_alone == 9) { # jacks or better, hold the cards
   foreach $num (@init_nums){ # find out what two cards they are
	   if($cards{$num} == 2 && $num =~ /^J|Q|K|A$/){
          foreach $pos (0,1,2,3,4){ # go through and keep them all
             if ($keep[$pos] =~ $num) {
                $keep2[$pos] = $keep[$pos];
                if ($debug) { print "JBkeep=$keep[$pos] num=$num "; }
                }
	         }
		   }
       }
   $draw_again = 1; # indicate we need to draw more cards
   }

if($leave_alone == 8) { # two pair, hold the cards
   foreach $num (@init_nums){ # find out what two sets of cards they are
	   if($cards{$num} == 2){
          foreach $pos (0,1,2,3,4){ # go through and keep them all
             if ($keep[$pos] =~ $num) {
                $keep2[$pos] = $keep[$pos];
                if ($debug) { print "2Pkeep=$keep[$pos] num=$num "; }
                }
	         }
		   }
       }
   $draw_again = 1; # indicate we need to draw more cards
   }

if($draw_again == 1) { # draw more cards using kept cards (keep2 variable)
   foreach $pos (0,1,2,3,4){  # make keep variable ready for check again
      if($keep2[$pos] ne ""){ $keep[$pos] = $keep2[$pos]; }
      else { $keep[$pos] = shift(@init_cards); } # pull another card
	  if ($debug) { print "$keep[$pos] "; }
	  }

   &find_wins(); # find any wins (subroutine)
   }

# now calculate the win amounts and display the winning had type

$balance = $balance - $coins_per_bet;
$win = 0;

if($straight == 1 && $flush == 1 && $royal == 1){
	$winmsg = "royal_flush!";
	$win = (800 * $coins_per_bet);
    $win_royals++;
	}
elsif($straight == 1 && $flush == 1){
	$winmsg = "straight_flush!";
	$win = (200 * $coins_per_bet);
    $win_sf++;
	}
elsif($fourofakind){
	$winmsg = "four_of_a_kind!";
	$win = (25 * $coins_per_bet);
    $win_4ofak++;
	}
elsif($threeofakind && $pair == 1){
	$winmsg = "full_house!";
	$win = (9 * $coins_per_bet);
    $win_fullh++;
	}
elsif($flush == 1){
	$winmsg = "flush!";
	$win = (6 * $coins_per_bet);
    $win_f++;
	}
elsif($straight == 1){
	$winmsg = "straight!";
	$win = (4 * $coins_per_bet);
    $win_s++;
	}
elsif($threeofakind){
	$winmsg = "three_of_a_kind!";
	$win = (3 * $coins_per_bet);
    $win_3ofak++;
	}
elsif($pair == 2){
	$winmsg = "two_pair!";
	$win = (2 * $coins_per_bet);
    $win_2p++;
	}
elsif($jacksorbetter == 1){
	$winmsg = "jacks_or_better!";
	$win = (1 * $coins_per_bet);
    $win_jb++;
	}
else {
	$winmsg = "nothing";
	}

$balance = $balance + $win;
$gamectr++;

# print a report
if ( (++$displayctr >= $display_every) ||
     ($gamectr >= $stop_at_games) ){
   $change = $balance - $last_bal;
   $last_bal = $balance;
   print "Games Played $gamectr\n";
   print "Start $starting_balance End Bal $balance Change=$change (bet $coins_per_bet)\n";
   print "Royals $win_royals SF $win_sf 4ofak $win_4ofak FullH $win_fullh\n";
   print " F $win_f S $win_s 3ofak $win_3ofak 2P $win_2p JorB $win_jb\n\n";
   $displayctr = 0;
   }

if ($debug) { print "       $winmsg  Win=$win Bal=$balance ($gamectr)\n"; }

}



sub find_wins {

foreach $sss (@init_suits){
	$suits{$sss} = 0;
	}

foreach $ccc (@init_nums){
	$cards{$ccc} = 0;
	}

foreach $pos (0,1,2,3,4){

  $card = $keep[$pos];

  ($n,$s) = split(/\./, $card);
  $suits{$s}++;
  $cards{$n}++;
  }


if ($debug) {

print "   ";

foreach $sss (@init_suits){
	print "$sss=$suits{$sss} ";
	}

print "\n   ";

foreach $ccc (@init_nums){
	print "$ccc=$cards{$ccc} ";
	}

print "\n";
} # end debug print

$jacksorbetter = 0;
$pair = 0;
$threeofakind = 0;
$fourofakind = 0;
$flush = 0;
$straight = 0;
$royal = 0;

$i = 0;
$i1 = 0;
$i2 = 0;
$i3 = 0;
$i4 = 0;

# If all suits are the same, indicate a flush
foreach $suit (@init_suits){
	if($suits{$suit} == 5){ $flush = 1; }
	}

# find the winners
foreach $num (@init_nums){
	if($cards{$num} == 2 && $num =~ /^J|Q|K|A$/){
		$jacksorbetter = 1;
		}
	if($cards{$num} == 2){
		$pair++;
		}
	if($cards{$num} == 3){
		$threeofakind = 1;
		}
 	if($cards{$num} == 4){
		$fourofakind = 1;
		}

    if($i > 12){ $i -= 12; }
	$i1 = $i + 1; if($i1 > 12){ $i1 -= 13;}
	$i2 = $i + 2; if($i2 > 12){ $i2 -= 13;}
	$i3 = $i + 3; if($i3 > 12){ $i3 -= 13;}
	$i4 = $i + 4; if($i4 > 12){ $i4 -= 13;}

	if($cards{$init_nums[$i]} &&
	   $cards{$init_nums[$i1]} && $init_nums[$i1] ne 'A' &&
	   $cards{$init_nums[$i2]} && $init_nums[$i2] ne 'A' &&
	   $cards{$init_nums[$i3]} && $init_nums[$i3] ne 'A' &&
	   $cards{$init_nums[$i4]}){

		$straight = 1;
		}

	if($cards{$init_nums[$i]} && $init_nums[$i] eq "10" &&
	   $cards{$init_nums[$i1]} && $init_nums[$i+1] eq "J" &&
	   $cards{$init_nums[$i2]} && $init_nums[$i+2] eq "Q" &&
	   $cards{$init_nums[$i3]} && $init_nums[$i+3] eq "K" &&
	   $cards{$init_nums[$i4]} && $init_nums[$i+4] eq "A"){
		$royal = 1;
		}
	$i++;

	}
 }


```

---

### Post by meborc on 2009-03-23
that is depressing... i keep loosing money, no matter what strategy i use :(

---

### Post by fixitdude on 2009-03-28
> **meborc said:**
> that is depressing... i keep loosing money, no matter what strategy i use :(I should say that in real life a lot of times you can play a perfect game at a real video poker machine with a good pay table for hours on end and get comped drinks. That's how you get ahead.

This program helps you to determine what a good pay table is.

Make sure you pick the best pay table in town, not just at one casino, look around other places first and sometimes only 4 or 8 machines will be set good! And drinks come faster sitting at a bar.

Then prepare to stick around, never leave until you are even or ahead and plan to possibly lose $100, that way you won't get nervous about being down and continue on to hopefully get even again.

The other possibility is that since you are playing a long time you might hit a royal or something and walk away with more.

Oh, and when drinking, figure your IQ drops about 30% so if you play a almost perfect game normally, don't bet large after a few drinks. Discipline helps, set some rules in your mind and stick to them.

Always tip your server/bartender!

---


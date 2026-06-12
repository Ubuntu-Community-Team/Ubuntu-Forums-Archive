---
title: "Does this website lock up Firefox for you?"
date: 2009-12-06
forum: Desktop Environments
---

### Post by mike984 on 2009-12-06
Whenever I go to the website [www.cookscountrytv.com](www.cookscountrytv.com) my Firefox locks up.  It's a website for a cooking show.

Is this locking up anyone else's Firefox?

---

### Post by User3k on 2009-12-06
Works fine for me, the video isn't loading though.

---

### Post by User3k on 2009-12-06
I take that back. When I close the tab for that website it freezes Firefox on me. 

Edit:I tried it twice and the same thing.

---

### Post by kelvin spratt on 2009-12-06
same as above

---

### Post by User3k on 2009-12-06
I tried the same link in Google Chrome and it doesn't do that.


Edit: [http://dev.chromium.org/getting-involved/dev-channel]("http://dev.chromium.org/getting-involved/dev-channel") If you want to use that website with Google Chrome. It has the Linux .deb beta packages towards the bottom.

---

### Post by mike984 on 2009-12-06
Should I file a bug with Firefox?

---

### Post by User3k on 2009-12-06
> **mike984 said:**
> Should I file a bug with Firefox?


It is probably the website itself, not really Firefox. They may have bad code or something at the website.

---

### Post by mike984 on 2009-12-06
Ok, thanks for testing this.

---

### Post by chillicampari on 2009-12-06
Firefox and Opera (10.01) are both locking up for me.

---

### Post by User3k on 2009-12-06
> **mike984 said:**
> Ok, thanks for testing this.

Your welcome. If that is a website you really want to use you might want to give Chrome a try with the links I posted above. I seem to bounce between both but Chrome, though it is beta, is working fine for me.

---

### Post by lisati on 2009-12-06
> **User3k said:**
> I take that back. When I close the tab for that website it freezes Firefox on me. 

Edit:I tried it twice and the same thing.

I tried opening in a new window. It locked up, and a forced quit closed both windows of FireFox......

---

### Post by lovinglinux on 2009-12-06
Is locking for me too. It opens fine, but suddenly locks Firefox. What is interesting is that I'm using NoScript and FlashBlock.

It is not locking Opera.

EDIT: strike that, Opera is locking too.

---

### Post by lovinglinux on 2009-12-06
The culprit is the flash content below:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=138863&stc=1&d=1260147266[/IMG]

Once I disable flash, it stops locking Firefox. I also tested it on a fresh FF profile with NoScript blocking everything and without any whitelisted site, in which case it was effectively blocked. Once I enable that content, it locks again. When I tried to right-click on that page, it locked my entire desktop.

EDIT: There was some sort of conflict between FlashBlock and NoScript. They both are blocking now.

Here is the source code of the page:

```

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1" />
        <title>Cook's Country TV</title>
        
        <link rel="stylesheet" type="text/css" href="css/main.css" />
        <link rel="stylesheet" type="text/css" href="css/contentslider.css" />
        
        <script type="text/javascript" src="/js/swfobject.js"></script>

        <script src="http://www.google-analytics.com/urchin.js" type="text/javascript"></script>
        <script type="text/javascript">
            try {
            _uacct = "UA-6984435-3";
            urchinTracker();
            } catch(err) {}
        </script>
        
        <script type="text/javascript">
            function bannerAd(bannerName, bannerURL)
            {
                urchinTracker('/bannerAD/'+bannerName);
                window.open(bannerURL);
            }
        </script>
        
        
    </head>
<body onload="checklogin('');  addToMember_Visits();">
<!-- Main content section -->
	<!-- BEGIN Masthead Include -->
	<!-- Sitewide header, above white content box -->

	<!-- Identifier MASTHEADINCLUDE_NAVSITE_CURRENTITEM: Used to highlight the proper tab in the navSite div -->
	<ul id="navCorp">
		<li id="atkLogo"><a href="http://www.americastestkitchen.com/corp/about-americastestkitchen.asp" class="americasTestKitchenBadge">America's Test Kitchen</a></li>
		<li class="cio"><a href="http://www.cooksillustrated.com">Cook's Illustrated</a></li>
		<li class="cco"><a href="http://www.cookscountry.com">Cook's Country</a></li>
		<li class="atk"><a href="http://www.americastestkitchen.com/">America's Test Kitchen TV</a></li>

		<li class="cctv"><a href="http://www.cookscountrytv.com">Cook's Country TV</a></li>
		<li class="bookstore"><a href="http://www.cooksillustrated.com/bookstore/">Bookstore</a></li>
		<li class="customerService"><a href="http://www.americastestkitchen.com/corp/customer_service.asp">Customer Service</a></li>
	</ul>


	<!-- End sitewide header -->
	
	<div id="cctvBanner">

		
		<a href="/"><img src="/images/common/logo_cctv.gif" id="cctvBannerImg" /></a>
		
		<div id="searchBox">Recipes That Work<sup>&reg; </sup><br />
			<form id="searchBoxForm" action="/search/default.asp" method="GET">
				<select name="searchcategory" id="searchcategory">
				    <option value="1" selected="selected">Recipes</option>
					<option value="14">Episodes</option>
					<option value="3">Equipment</option>

					<option value="2">Taste Tests</option>					
                </select>
				<input type="text" class="shadowedInput" name="stext" />
				<input type="image" src="/images/common/btn_search.gif" alt="Search" class="searchButtonInput" />
			</form>
		</div>
			
		<a href="https://w1.buysub.com/servlet/OrdersGateway?cds_page_id=19245&cds_mag_code=CCY&cds_response_key=IJB08A010" id="magCoverLink"><img src="/images/common/headerCover.gif" id="ccHeaderMag" /></a>
		<a href="https://w1.buysub.com/servlet/OrdersGateway?cds_page_id=19245&cds_mag_code=CCY&cds_response_key=IJB08A010" id="magSubscribeLink">Subscribe</a>

		
	</div>

	<!-- End content header -->

	<!-- Main content section -->

	
	<div id="container">

		<!-- Wide right column -->

		<div id="rightCol">


			

<!-- END Masthead Include -->



<!-- Javascript to track Members unique Visits -->

<script type="text/javascript">


var addToMem=true;	

	function addToMember_Visits() {
	 if(addToMem) {	
		var xmlHttp;
		try {  // Firefox, Opera 8.0+, Safari
			xmlHttp=new XMLHttpRequest();
		}
		catch (e) {  // Internet Explorer
			try {
				xmlHttp=new ActiveXObject("Msxml2.XMLHTTP");
			}
			catch (e) {
				try {
					xmlHttp=new ActiveXObject("Microsoft.XMLHTTP");
				}
				catch (e) {
					alert("Your browser does not support AJAX!");
					return false;
				}
			}
		}		
		xmlHttp.onreadystatechange=function()
			{
				if(xmlHttp.readyState==4) {			
					if(xmlHttp.responseText);							
				}
			}	
		targetURL = "/includes/member_visits.asp?memberId=";
		xmlHttp.open("GET",targetURL,true);
		xmlHttp.send(null); 
	 }	
	}
	
	 function addtoMemTable_False()
		  {
			 addToMem=false;
		  }
	window.onload = addToMember_Visits;
	
	//-->
</script>


	
<div id="featureStage">
  <div class="slideShow">

      

	
				<div class="contentdiv"> 
				<a href="#"><img src="http://www.cooksillustrated.com/images/document/407x291_SFS_Mustard_Glazed_Grilled_Pork_Loin.jpg" alt="Grilled Mustard-Glazed Pork Loin" class="featureImg" /></a>
					<div class="featureText">	
						<h2>Grilled Mustard-Glazed Pork Loin</h2>
						<p>We dress up pork roast by giving it a flavorful, deeply caramelized crust on the grill and serve it with a savory-sweet mustard glaze.
</p>
			
	
						<a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=8461">Read More</a>		
					</div>
				</div>

	
				<div class="contentdiv"> 
				<a href="#"><img src="http://www.cooksillustrated.com/images/document/407x291_SFS_Ultimate_Cinnamon_Buns.jpg " alt="Ultimate Cinnamon Buns" class="featureImg" /></a>
					<div class="featureText">	
						<h2>Ultimate Cinnamon Buns</h2>
						<p>Ultimate cinnamon buns should be tender, gooey, and unapologetically large. Tragically, most recipes yield lean buns&#8212;and ultimate disappointment. </p>

			
	
						<a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=17864">Read More</a>		
					</div>
				</div>

	
				<div class="contentdiv"> 
				<a href="#"><img src="http://www.cooksillustrated.com/images/document/407x291_SFS_Chili_con_Carne.jpg" alt="Chili Con Carne" class="featureImg" /></a>
					<div class="featureText">	
						<h2>Chili Con Carne</h2>
						<p>We create a simple, authentic-tasting version of this Tex-Mex classic using supermarket ingredients. </p>

			
	
						<a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=12089">Read More</a>		
					</div>
				</div>

	
				<div class="contentdiv"> 
				<a href="#"><img src="http://www.cooksillustrated.com/images/document/407x291_SFS_Tunnel_of_Fudge_Cake.jpg " alt="Tunnel of Fudge Cake" class="featureImg" /></a>
					<div class="featureText">	
						<h2>Tunnel of Fudge Cake</h2>
						<p>The original recipe relied on a now-defunct ingredient. But that didn&#8217;t mean this historic cake needed to be out of production too.</p>

			
	
						<a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=8686">Read More</a>		
					</div>
				</div>
		
			
  </div>	
			<ul id="slideNav">
			</ul>
			
		<a href="/aboutus/"><img src="images/kitchenTourLink.gif" alt="Tour Our Kitchen" class="kitchenTourLink" /></a>							
</div>

				
				<a name="video" id="video"></a>

			<!-- End top section -->



		  <div id="freeAccess">
		  		Get <span>Free Access</span> to every recipe and rating from the current season!				
				<form action="default.asp" method="post" id="paywallSignupForm" name="paywallSignupForm" onsubmit="addToRegistration_Abandonment('www.cookscountrytv.com/register/default.asp?Incode=CCYTVHome');">
					<input type="hidden" name="Incode" value="CCYTVHome">	
					<input type="text" class="shadowedInput" name="email" id="email" value="Enter E-mail Address" onfocus="controlOnFocus(this, 'Enter E-mail Address'); " onblur="controlOnBlur(this, 'Enter E-mail Address');" /><input type="image" src="/images/common/btn_go.gif" onclick="return checkbae();" />						
					<input type="hidden" name="button" value="submit">

				</form>
			  <br />
				    <a id="howWeUseEmailLink" href="javascript:void(0)" onclick="window.open('/includes/useEmail.asp','window', 'width=320, height=220');">How we use your email address</a>		        
			</div>
		
			<!-- Begin Flash Player -->
			<div class="pageSection">
			
			 
 <div id="flash_player"> 			 
		<object classid="clsid:d27cdb6e-ae6d-11cf-96b8-444553540000" codebase="http://fpdownload.macromedia.com/pub/shockwave/cabs/flash/swflash.cab#version=8,0,0,0" width="496" height="377" >
			<param name="movie" value="/preroll/tracking2.swf" />

			<param name="FlashVars" value="videos=/preroll/videos.xml" />
			<embed src="/preroll/tracking2.swf" FlashVars="videos=/preroll/videos.xml" width="496" height="377" type="application/x-shockwave-flash" pluginspage="http://www.macromedia.com/go/getflashplayer" />
		</object>
</div>		
				<div id="underwriters">
					<h2>Our Underwriters</h2>
					<p><a href="./underwriters/">Our underwriters</a> make it possible to bring you the Cook's Country TV series on public television.</p>
					<ul class="underwriterLogos">

					    <li id="dcs"><a href="http://www.dcsappliances.com/" target="_blank"><img src="images/common/x.gif" alt="DCS by Fischer & Paykel" /></a></li>
                        <li id="viva"><a href="http://www.vivatowels.com" target="_blank"><img src="images/common/x.gif" alt="Viva Towels" /></a></li>
                        <li id="cooking"><a href="http://www.cooking.com/" target="_blank"><img src="images/common/x.gif" alt="Cooking.com" /></a></li>
					    <li id="choreboy"><a href="http://www.choreboyscrubbers.com/" target="_blank"><img src="images/common/x.gif" alt="Chore Boy Scrubbers" /></a></li>
					    <li id="idaho"><a href="http://idahopotato.com/" target="_blank"><img src="images/common/x.gif" alt="Cooking.com" /></a></li>					 
					    <li id="valley"><a href="http://www.valleyfig.com/" target="_blank"><img src="images/common/x.gif" alt="Valley Fig Growers" /></a></li>
                    </ul>
					<!--<a href="http://www.whiteflowerfarm.com/"><img src="images/marketing/logo_whiteflowerHome.jpg" alt="White Flower Farm" /></a>-->
				</div>

				
				
				<div style="clear: left;"></div>
			</div>
			<!-- End teaser lists -->
			<!-- Inside the Test Kitchen and video player quarter-sections -->
			<div class="pageSection">
				<div id="welcomeToCCTV">
				<div id="aboutCCTV">
						<img src="/images/chrisAndBridget.jpg" width="168" height="168" />
						<ul>

							<li><a href="aboutus/default.asp#cast">Meet the Cast</a></li>
							<li><a href="aboutus/default.asp">Kitchen Tour</a></li>
							<li><a href="http://www.americastestkitchen.com/corp/events.asp" target="_blank">Events &amp; Appearances</a></li>
							<li><a href="cookware/default.asp">Buy Rated Cookware</a></li>
						</ul>
				  </div>

					<h2>What is Cook's Country Television all about?</h2>
					<p><em>Cook's Country from America's Test Kitchen</em> uncovers the best of American home cooking. Our recipes are developed through in-depth kitchen testing. The result: foolproof recipes you can trust to work the first time&#8212;and every time. </p>
					
					<p><em>Cook's Country from America's Test Kitchen</em> features the cast and crew of America's Test Kitchen, the top-rated cooking show on public television&#8212;now in its ninth season. Our show, now in its second season, is filmed in a renovated 1806 farmhouse with a full working test kitchen.</p>
					
					<p>Watch us update traditional American recipes&mdash;everything from <a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=12089">Chili Con Carne</a> and <a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=7646">Mile-High Lemon Meringue Pie</a> to  <a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=17272">Cider-Braised Pork Chops</a> and <a href="http://www.cookscountrytv.com/recipes/detail.asp?docid=17864">Ultimate Cinnamon Buns</a>. You'll learn what makes a recipe succeed (or fail) as well as which kitchen tools, cookware, and supermarket ingredients have won our independent tests. </p>

					<p>Join us every week as we bring the pages of <em>Cook's Country</em> magazine into your home.</p>
				</div>
		<div id="microsite">	
            <h2>Q&A with<br />Christopher Kimball</h2>
            <p>

            	Check out <a href="http://www.americastestkitchen.com/OnlineQandA/archive.aspx">archives</a> of past live online Q&A sessions. <a href="http://www.americastestkitchen.com/OnlineQandA/?Incode=M9GJHSW00">Sign up to be alerted</a> when we schedule the next Q&A with Christopher Kimball.
            </p>
            
        </div>
				
		</div>					
			
			<div class="pageSection lastPageSection">	
				<div id="bigAd">

					<p class="bigAdHeadline">Get a <span>Free Trial Issue</span> of Cook's Country Magazine</p>
					<img src="/images/marketing/ads/ccy_ftform_magCover.jpg" id="bigAdCover" />
					<p class="bigAdText"><span>Yes!</span> <strong>Please send my FREE TRIAL ISSUE of <em>Cook's Country</em> Magazine</strong>.
						If I like it, I will pay just $19.95 for one full year (six issues, including my FREE TRIAL issue) and save 33% off the newsstand price of $29.70. 
						Otherwise, I'll write cancel on the invoice, return it, and owe nothing at all.</p>

					<img src="/images/ccy_ftform_B30M_Suppers.jpg" width="225" height="165" id="bigAdPremium" />
					<!-- Insert CDS Form -->
					<form method="post" name="botform" onsubmit="pop_conf(); return false;">
						<div class="bigAdLeftFieldset">
                            <input type="TEXT" name="cds_name" value="Name" id="Name" class="shadowedInput" onfocus="controlOnFocus(this, 'Name'); " onblur="controlOnBlur(this, 'Name');" />
                            <input type="TEXT" name="cds_address_1" value="Address (Line 1)" id="Address" class="shadowedInput" onfocus="controlOnFocus(this, 'Address (Line 1)'); " onblur="controlOnBlur(this, 'Address (Line 1)');" />
                            <input type="TEXT" name="cds_address_2" value="Address (Line 2)" id="Address2" class="shadowedInput" onfocus="controlOnFocus(this, 'Address (Line 2)'); " onblur="controlOnBlur(this, 'Address (Line 2)');" />
                        </div>
                        <div class="bigAdRightFieldset">

            
                            <input type="TEXT" name="cds_city" value="City" id="City" class="shadowedInput" onfocus="controlOnFocus(this, 'City'); " onblur="controlOnBlur(this, 'City');" />
                            <select name="cds_state" id="State" class="shadowedInput">
                                <option value="">State</option>
                                <option value="AL">AL</option>
                                <option value="AK">AK</option>
                                <option value="AZ">AZ</option>
                                <option value="AR">AR</option>

            
                                <option value="CA">CA</option>
                                <option value="CO">CO</option>
                                <option value="CT">CT</option>
                                <option value="DE">DE</option>
                                <option value="DC">DC</option>
                                <option value="FL">FL</option>

            
                                <option value="GA">GA</option>
                                <option value="HI">HI</option>
                                <option value="ID">ID</option>
                                <option value="IL">IL</option>
                                <option value="IN">IN</option>
                                <option value="IA">IA</option>

            
                                <option value="KS">KS</option>
                                <option value="KY">KY</option>
                                <option value="LA">LA</option>
                                <option value="ME">ME</option>
                                <option value="MD">MD</option>
                                <option value="MA">MA</option>

            
                                <option value="MI">MI</option>
                                <option value="MN">MN</option>
                                <option value="MS">MS</option>
                                <option value="MO">MO</option>
                                <option value="MT">MT</option>
                                <option value="NE">NE</option>

            
                                <option value="NV">NV</option>
                                <option value="NH">NH</option>
                                <option value="NJ">NJ</option>
                                <option value="NM">NM</option>
                                <option value="NY">NY</option>
                                <option value="NC">NC</option>

            
                                <option value="ND">ND</option>
                                <option value="OH">OH</option>
                                <option value="OK">OK</option>
                                <option value="OR">OR</option>
                                <option value="PA">PA</option>
                                <option value="RI">RI</option>

            
                                <option value="SC">SC</option>
                                <option value="SD">SD</option>
                                <option value="TN">TN</option>
                                <option value="TX">TX</option>
                                <option value="UT">UT</option>
                                <option value="VT">VT</option>

            
                                <option value="VA">VA</option>
                                <option value="WA">WA</option>
                                <option value="WV">WV</option>
                                <option value="WI">WI</option>
                                <option value="WY">WY</option>
                            </select>

            
                            <input type="TEXT" name="cds_zip" maxlength=20 value="Zip Code" id="Zip" class="shadowedInput" onfocus="controlOnFocus(this, 'Zip Code'); " onblur="controlOnBlur(this, 'Zip Code');" />
                        </div>
                        <div class="bigAdEmail">
                            <input type="TEXT" name="cds_email" value="E-mail (required)" id="Email" class="shadowedInput" onfocus="controlOnFocus(this, 'E-mail (required)'); " onblur="controlOnBlur(this, 'E-mail (required)');" />
                            <a id="howWeUseEmailLink" href="javascript:void(0)" onclick="window.open('includes/useEmail.asp','window', 'width=320, height=220');">How we use your email address</a> 
                        </div>
                        <div id="bigAdButtons">
                            <a href="javascript:void(0);" onclick="javascript:pop_conf();"><img src="images/common/btn_freeTrial.gif" id="btnFreeTrial" border="0" /></a>
							OR <a href="javascript:void(0);" onclick="javascript: collectcdsb('https://w1.buysub.com/servlet/PrePopGateway?cds_page_id=67061&cds_mag_code=CCY&amp;cds_response_key=IJH09JB0F');"><img src="images/common/btn_freeGift.gif" id="btnFreeGift" border="0" /></a> 
                        </div>

					</form>
					<p class="bigAdFooter">Offer valid in U.S. only. <a href="https://w1.buysub.com/servlet/OrdersGateway?cds_mag_code=CCY&cds_page_id=19245" target="new">Canadian and International Subscriptions</a></p>
				</div>
			<!-- end big ad -->
			</div>
				</div>
		<!-- End right column -->

	    

		<!-- Narrow left column with login box, subscription info and lists -->

		<div id="leftContentCol">
			<div id="loginNavLinksFinder">
				<ul id="loginRegisterLinks">
					
						<li id="loginLink"><a href="/auth/">Login</a></li>
						<li><a href="/register/">Register</a></li>
					
				</ul>

				
				<ul id="siteNav">
					<li><a href="/episode/">Episodes</a></li>
					<li><a href="/recipes/">Recipes</a></li>
					<li><a href="/equipment/">Equipment Reviews</a></li>
					<li><a href="/tastetests/">Taste Tests</a></li>
				</ul>

				<ul id="infoLinks">
					<li><a href="/aboutus/">About Our TV Show</a></li>
					<li><a href="/cookware/default.asp">Buy Rated Cookware</a></li>
					<li><a href="/videotips/default.asp">Video Tips &amp; Techniques</a></li>
					<li><a href="http://www.americastestkitchen.com/ibb/categoryindex.aspx?boardID=1" target="_blank">Bulletin Board</a></li>

					<li><a href="/enewsletter/">Free Newsletter</a></li>
				</ul>
				
				   <form method="get" action="http://www.tracmedia.com/lol/cooksCountry/"  id="stationFinder" target="_blank" onSubmit="return redirectOutput(this);">
				  Find out when our show airs in your area:
				   <input type="hidden" name="searchBy" value="Zip">
				   <input type="text"  name="zipCode" id="zipCode" value="Zip Code" class="shadowedInput" /><input type="image" name="submit" src="/images/common/btn_goStationFinder.gif" />
				</form>
			</div>

			<div id="dvdAndBookSet">
				<a href="https://m1.buysub.com/webapp/wcs/stores/servlet/GeneralCheckoutView?catalogId=11551&storeId=11551&productId=706423&gPre=CYTV09W&text=209_601&desc=Cook%27s%20Country%20TV%20Season%20Two%20Order%20Form&categoryIdUp=&bsMap=33_221_221_252&pst=1&sourcekey=CJ09010LA"><img src="/images/marketing/ads/cctv_dvdCompanionS02.png" class="seasonTwo" alt="Season Two TV Companion and DVD Set" style="border: 0;" /></a>
			
				<a href="https://m1.buysub.com/webapp/wcs/stores/servlet/GeneralCheckoutView?catalogId=11551&storeId=11551&productId=497723&gPre=CN02W&text=209_601&desc=The%20Cook's%20Country%20Cookbook%20and%20DVD%20Order%20Form&bsMap=235_161_393_179&sourcekey=CJ08010LA"><img src="/images/marketing/ads/cctv_dvdCompanionS01.png" class="seasonOne" alt="Season One TV Companion and DVD Set" style="border: 0;" /></a>
			</div>
			<div id="atkSpecialOffers">
				<strong>Special Offers from America's Test Kitchen</strong>
				<ul>
					<li><a href="https://www.cookscountry.com/cds_auth/signup/default/join_step1.asp?Incode=M00JHLA00">CooksCountry.com Free Trial Membership</a></li>

					<li><a href="https://w1.buysub.com/servlet/OrdersGateway?cds_page_id=19245&cds_mag_code=CCY&cds_response_key=IJL09A010">Subscribe to <em>Cook's Country</em> magazine</a></li>
					<li><a href="https://w1.buysub.com/servlet/OrdersGateway?cds_mag_code=ECI&cds_page_id=60455&cds_response_key=IJH09CL00">Subscribe to <em>Entertaining</em> magazine</li>
					<li><a href="https://w1.buysub.com/servlet/OrdersGateway?cds_mag_code=CID&cds_page_id=13331&cds_response_key=IJL09A010">Subscribe to <em>Cook's Illustrated</em> magazine</a></li>

					<li><a href="https://m1.buysub.com/webapp/wcs/stores/servlet/GeneralCheckoutView?catalogId=11551&storeId=11551&productId=554223&gPre=CY04&text=203_600&desc=Cook%27s%20Country%202008%20Annual%20Order%20Form&categoryIdUp=200392&bsMap=81_158_254_181&pst=1&sourcekey=CJ09020LA"><em>Cook's Country</em> 2008 Annual</a></li>
					<li><a href="http://www.cooksillustrated.com/bookstore.asp">Browse Our Bookstore</a></li>
				</ul>
			</div>
			

		</div><!-- End left column -->
<div class="clearForFooter">&nbsp;</div>

</div><!-- End center content section -->

	

<!-- Content footer section with curved corners -->
	
	

<div id="contentFooter">
		
	<a href="http://www.aptonline.org"><img src="/images/common/logo_apt.gif" alt="American Public Television" id="aptFooterLogo" /></a>
		
	<a href="http://www.americastestkitchen.com/corp/about-americastestkitchen.asp"><img src="/images/common/americas_test_kitchen_badge.png" alt="America's Test Kitchen" id="atkFooterLogo" /></a>
		
	
	<ul id="corpFooter">
			
		<li class="footerNavFirst"><a href="http://www.americastestkitchen.com/corp/about-americastestkitchen.asp">About Us</a></li>
					
		<li><a href="/privacy/">Privacy Policy</a></li>

			
		<li><a href="http://www.americastestkitchen.com/corp/reporting-policy.asp">Re-Use Policy</a></li>
			
		<li><a href="http://www.americastestkitchen.com/corp/presscontact.asp">Press Contact</a></li>
			
		<li><a href="http://www.americastestkitchen.com/corp/customer_service.asp">Customer Service</a></li>
			
		<li><a href="http://www.americastestkitchen.com/corp/jobs.asp">Job Opportunities</a></li>
			
		<li><a href="http://www.americastestkitchen.com/corp/events.asp">Events &amp; Appearances</a></li>

			
	
	</ul>
		
	
	<ul id="corpFooter">
			
	
		<li class="footerNavFirst"><a href="http://www.americastestkitchen.com/sweepstakes/winners.aspx">Sweepstakes</a></li>
			
		<li><a href="/enewsletter/">E-mail Newsletter</a></li>
			
		<li><a href="https://w1.buysub.com/servlet/OrdersGateway?cds_mag_code=CID&cds_page_id=13377&cds_response_key=IJF08A0F0">COOK'S ILLUSTRATED Magazine</a> <span style="color: #fff;"> | </span> <a href="https://www.cooksillustrated.com/default.asp?Extcode=M00JHFA00">Website</a></li>

			
		<li><a href="https://w1.buysub.com/servlet/OrdersGateway?cds_page_id=19245&cds_mag_code=CCY&cds_response_key=IJF08A0F0">COOK'S COUNTRY Magazine</a> <span style="color: #fff;"> | </span> <a href="https://www.cookscountry.com/default.asp?Extcode=M00JHFA00">Website</a></li>
		
	</ul>

	
</div><!-- End content footer section -->
	
	
<!-- Paywall-->
	
<div id="paywallLoginSignupHomeDiv" style="display:none;"><span class="StartYourFreeTrial">Login now for FREE access to every recipe and rating from the current season of Cook&rsquo;s CountryTV.</span>

  <form action="auth/login_process.asp" method="POST" id="paywallLoginForm">
		<span class="memberTextHeader">Member Login</span>
		<input type="hidden" name="docid" id="docid" value="" />
		<input type="text" name="email" class="shadowedInput" value="Login" onfocus="controlOnFocus(this, 'Login'); " onblur="controlOnBlur(this, 'Login');" />
		<input type="image" alt="Login" src="/devel/cctv/images/text/btn_login.gif" class="loginButton" />
		
		
			
		
		<a href="/redesign/cds_auth/forgot_password.asp">Forgot your password?</a><br />
		  
	</form>
	
	<div id="paywallSignupDiv">

		<span class="memberTextHeader">Not Yet Registered?</span>
		<ul>
			<li>IT&#8217;S FAST AND IT&#8217;S FREE</li>
		
		</ul>
		<form action="/redesign/join_freetrial14_1.asp" method="post" id="paywallSignupForm">
			<input type="text" value="Enter Email Address" name="sCustomerEmail" class="shadowedInput" />
			<input type="image" alt="Start Now" id="btnStartNow" src="/devel/cctv/images/common/btn_startNow.gif" />
		</form>

		
		<br /> <br /><center><a href="javascript:login('hide');">close</a></center>	
  </div>

</div>		




	
<script type="text/javascript" src="/js/page_util.js"></script>
    
<script type="text/javascript" src="http://ajax.googleapis.com/ajax/libs/jquery/1.2.6/jquery.min.js"></script>
	
<script type="text/javascript">
        
	$(document).ready(function(){
            
		var lastVal = ""; 
		// Global var to hold the last state of a field contents
            
		$(".shadowedInput").focus(function(){
                
			lastVal = $(this).val();
                
			$(this).val("");
            
		});
           
		$(".shadowedInput").blur(function(){
                
			if ($(this).val() == ""){
                
				$(this).val(lastVal);
                
			} else { 
                    
				$(this).unbind('focus');
                
			};
            
		});
     
	});
    
</script>
<script type="text/javascript">
	var gaJsHost = (("https:" == document.location.protocol) ? "https://ssl." : "http://www.");
	document.write(unescape("%3Cscript src='" + gaJsHost + "google-analytics.com/ga.js' type='text/javascript'%3E%3C/script%3E"));
	
	try {
		var pageTracker = _gat._getTracker("UA-6984435-1");
		pageTracker._trackPageview();
	} catch(err) {}
</script> 
	

<!-- End footer -->

<script>
<!--
var addToReg=true;	
var sPath = window.location.pathname;
				//var sPage = sPath.substring(sPath.lastIndexOf('\\') + 1);
				//var sPage = sPath.substring(sPath.lastIndexOf('//') + 1);

	function addToRegistration_Abandonment(sPage) {
	 if(addToReg) {	
		var xmlHttp;
		try {  // Firefox, Opera 8.0+, Safari
			xmlHttp=new XMLHttpRequest();
		}
		catch (e) {  // Internet Explorer
			try {
				xmlHttp=new ActiveXObject("Msxml2.XMLHTTP");
			}
			catch (e) {
				try {
					xmlHttp=new ActiveXObject("Microsoft.XMLHTTP");
				}
				catch (e) {
					alert("Your browser does not support AJAX!");
					return false;
				}
			}
		}		
		xmlHttp.onreadystatechange=function()
			{
				if(xmlHttp.readyState==4) {			
					if(xmlHttp.responseText);							
				}
			}	
		targetURL = "/includes/registrationAbandonment.asp?email=" + document.getElementById("email").value + "&" +  "abandon_page=" + sPage;
		xmlHttp.open("GET",targetURL,true);
		xmlHttp.send(null); 
	 }	
	}
	
	 function addtoRegTable_False()
		  {
			 addToReg=false;
		  }		  
	
	-->
</script>

<script language="JavaScript1.2">
// VALIDATION FOR CENTER WELL BOX

//Advanced Email Check credit-
//By JavaScript Kit (http://www.javascriptkit.com)
//Over 200+ free scripts here!

var testresults
function checkemail(){
var str=document.paywallSignupForm.email.value
var filter=/^([\w-]+(?:\.[\w-]+)*)@((?:[\w-]+\.)*\w[\w-]{0,66})\.([a-z]{2,6}(?:\.[a-z]{2})?)$/i
if (filter.test(str))
testresults=true
else{
alert("Please enter a valid email address.")
testresults=false
}
return (testresults)
}
</script>

<script>
function checkbae(){
if (document.layers||document.getElementById||document.all)
return checkemail()
else
return true
}
</script>

<script type="text/javascript" src="/js/jquery.cycle.js"></script>
<script type="text/javascript">
$(document).ready(function() {    
    
	$(".contentdiv").attr("style","visibility: visible;");
    
	function onClick() { 
   	   $(".slideShow").cycle('pause');
   	   $(".slideShow").cycle('stop');
   	};
	
	$('.slideShow').cycle({
		fx:'fade',
		timeout: 8000,
		pagerClick: onClick,
		pager: '#slideNav',
		pagerAnchorBuilder: function(idx, slide) {
			return '<a href="#" class="slideControl" onclick="javascript:this.blur();"><img src="images/common/x.gif"></a>';
		}
	});    
});
</script>
		
</body>

</html>

```

---

### Post by akashiraffee on 2009-12-06
OMG PEOPLE STOP IT NOW!!! IT'S GONNA LOCK UP FIREFOX!!!  :popcorn:  Really it will.  Don't do it.

You need to kill the process.  Go to System->Administration->System Monitor and click on the processes tab.  Scroll down until you reach filefox.  Click it.  Now the "End Process" button lights up.  Kill all the firefoxes you can.

---

### Post by alexfish on 2009-12-06
> **mike984 said:**
> Whenever I go to the website [www.cookscountrytv.com]("http://www.cookscountrytv.com") my Firefox locks up.  It's a website for a cooking show.

Is this locking up anyone else's Firefox?

Hi just got back home/ been away for  two weeks

  ran the update manager  



  rebooted  

  lots of people use to say it was the best thing since "Sliced Bread"

   well I can tell you this thing ain't even pored me a " Glass of Water "yet

   going back to Opera / its platform                            independent


and wish I could shove Flash back where it belongs   ,,,,,,,,  up its   "     "

---

### Post by lovinglinux on 2009-12-06
> **alexfish said:**
> going back to Opera / its platform independent

Good luck, this has nothing to do with the browser. Opera is locking too.

---

### Post by alexfish on 2009-12-06
> **lovinglinux said:**
> Good luck, this has nothing to do with the browser. Opera is locking too.

now you tell me

  Brakes are on 

  What next

Thanks in advance

alexfish

just been here

 [http://www.forevergeek.com/2004/12/make_firefox_faster/](http://www.forevergeek.com/2004/12/make_firefox_faster/)

   Not Going back to Opera Yet

---

### Post by mindmachine on 2009-12-27
Man, how many of us have hit this page until now?? How many have been stuck with a crashed browser just for curiosity reasons :lolflag:???
For a page they would never ever visit in their whole life, for some cooking stuff... LOL. This is great if you need to increase page ranking of your site. The site code is worth a million bucks....

---


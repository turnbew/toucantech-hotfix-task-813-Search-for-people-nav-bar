FOR PRIVACY AND CODE PROTECTING REASONS THIS IS A SIMPLIFIED VERSION OF CHANGES AND NEW FEATURES

TASK DATE: 06.11.2017 - FINISHED: 06.11.2017

TASK LEVEL: (EASY)  

TASK SHORT DESCRIPTION: 813 (Search for people nav bar)

GITHUB REPOSITORY CODE: hotfix/task-813-Search-for-people-nav-bar

CHANGES
 
	IN FILES: 
	
		
		header.html
		
			CHANGED CODE:
			
				FROM: 
				
					<div class="col-md-1 col-md-offset-1 action_icons">{{ messaging:icon }}</div>
				
				TO: 
				
					<div class="col-md-1 col-md-offset-1 action_icons">{{ messaging:bootstrap_icon glyphicon='envelope' }}</div>

			
			
			
		search.js

			ADDED CODE: 
			
				.focusin(function() {
					if ($(this).val() == 'Search for people') {
						$(this).val('');
						$(this).css({'border-bottom': 'solid 1px'});
					}
				})
				.focusout(function() {
					if ($(this).val() == '') {
						$(this).val('Search for people');
						$(this).css({'border-bottom': 'none'}, {'outline' : 'none'});	
					}
				})
				
				
				
				
		general.css
		
			CHANGED/ADDED CODE 1: 
			
				#header_search_input {
					padding-left: 2px; 
					padding-right: 2px; 
					margin-left: -15px;
					border-bottom: none;
					outline: none;
					-webkit-border-radius: 0px;
					-moz-border-radius: 0px ;
					border-radius: 0px ;	
				}			
			
			ADDED CODE 2: 
			
				.envelope-glyphicon,
				.envelope-glyphicon-count {
					display: inline-block;
					width: 16px !important;
					height: 21px !important;
					padding: 2px 5px 0px 0px;
					margin-top:5px;
					vertical-align: text-bottom !important;
					text-align: center !important;
					font-size: 15px;
				}
				.envelope-glyphicon a,
				.envelope-glyphicon-count a {
					position: absolute;
					z-index: 50;
					font-size: 10px;
					text-shadow: 0px 0px 6px;
					font-weight: bold;
					margin-top: -21px;
					margin-left: -5px;
					height: 21px !important;
					width: 16px !important; 
					text-decoration: none !important;	
				}

				
				
				
		plugin.php
		
			ADDED CODE: 
			
				public function bootstrap_icon() 
				{
					$glyphicon = $this->attribute('glyphicon', 'envelope');
					
					$this->load->model('messages');
					$count = $this->messages->get_unread_message_count();
					
					$theme_color = ($this->settings->get('theme_colour') ==  $this->settings->get('theme_menu_text_colour'))
											? $this->settings->get('theme_colour')
											: $this->settings->get('theme_menu_text_colour');
					
					.................
				}

# LeagueOfLegends_RunesBreakdown

Attemp to create CSV from league of legends API containing related features needed to do prediction and make an interactive plots about runes.

Using riotWatcher package

1 Parse API of different ranks (Bronze, Silver, Gold, Platnium, Diamond, Masters, Challenger)

2 Create a webpage displaying educational statisics of runes depending of various variables. 

     Future Projects with data collected: 
     Create CSV for multi-class classification
     Attemp to create a model to predict players rank based on information such as 
          cs/min, kda, win percentages, which champions are played

TODO: ~~Current complications: ~~

Publically accessable ranks are Master and Challengers queues. To acccess Bronze, Silver, Gold, Plat, and Diamond queues I need to grab players in each of those ranks and then collect the corresponding league IDS. 

     1. Do summoner.by_name(region, summoner_name) for selected players in each of those ranks
          ex, summoner.by_name("na1", hissolitude)          
                         {
                         
              "profileIconId": 3186,
              
              "name": "HisSolitude",
              
              "summonerLevel": 42,
              
              "accountId": 33279580,
              
              "id": 20359886,
              
              "revisionDate": 1513142165000
              
          }
          
     2. Using the id we can do league.by_summoner(region,id) to get a the league the player is in, which includes 
     data of all players in that league. We can then grab corresponding data the same way we did for challenger and masters.
This issue is fixed by using riots seed data, found at https://s3-us-west-1.amazonaws.com/riot-developer-portal/seed-data/matches10.json
          
UPDATE 1: December 25th 2017
     Finished collecting for each user : accountIds,summonerIds,Top 3 Champions played and their scores, Champion Mastery score, and rank:  
     TODO: ~~Collect recent match history data and store relevant statistics as well as rune data.
     
UPDATE 2: Dec 27th 2017  
     Finished collecting match history data for 40,000 matchIds. We get 399901 data points! The corresponding CSV file is mergedStatistics.csv.. I have some trouble with errors in the beginning so I ran the script multiple times but in the end I removed any duplicates and "NA" perk values. See dataScrapping/getMatchStats.py for more information.
     TODO: Create a beautiful interactive page!!

SELECT COUNT(name) 
FROM video_games 
WHERE 
    game_developer IN (
        SELECT name 
        FROM game_developers 
        WHERE state = 'California'
    );

SELECT 
	g.address, 
	g.city, 
	g.state, 
	g.country 
FROM 
	video_games AS v 
INNER JOIN 
	game_developers AS g 
ON 
	g.name = v.game_developer AND 
	g.state = (
		SELECT g.state 
		FROM 
			game_developers AS g 
		INNER JOIN 
			video_games AS v 
		ON 
			g.name = v.game_developer 
		GROUP BY 
			g.state 
		ORDER BY 
			COUNT(v.name) DESC 
		LIMIT 1, 1
	) 
ORDER BY 
	v.release_date DESC 
LIMIT 1;

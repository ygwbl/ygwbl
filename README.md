![Anurag's GitHub stats](https://github-readme-stats.vercel.app/api?username=ygwbl&show_icons=true)
# Visit https://github.com/lowlighter/metrics#-documentation for full reference
name: Metrics
on:
  # Schedule updates (each hour)
  schedule: [{cron: "0 * * * *"}]
  # Lines below let you run workflow manually and on each commit
  workflow_dispatch:
  push: {branches: ["master", "main"]}
jobs:
  github-metrics:
    runs-on: ubuntu-latest
    permissions:
      contents: write
    steps:
      - uses: lowlighter/metrics@latest
        with:
          # Your GitHub token
          # The following scopes are required:
          #  - public_access (default scope)
          # The following additional scopes may be required:
          #  - read:org      (for organization related metrics)
          #  - read:user     (for user related data)
          #  - read:packages (for some packages related data)
          #  - repo          (optional, if you want to include private repositories)
          token: ${{ secrets.METRICS_TOKEN }}

          # Options
          user: ygwbl
          template: classic
          base: header, activity, community, repositories, metadata
          config_timezone: Asia/Shanghai
          plugin_achievements: yes
          plugin_achievements_display: detailed
          plugin_achievements_secrets: yes
          plugin_achievements_threshold: C
          plugin_discussions: yes
          plugin_discussions_categories: yes
          plugin_isocalendar: yes
          plugin_isocalendar_duration: half-year
          plugin_lines: yes
          plugin_lines_history_limit: 1
          plugin_lines_repositories_limit: 4
          plugin_lines_sections: base
          plugin_lines_skipped: 1
          plugin_music: yes
          plugin_music_limit: 4
          plugin_music_provider: apple
          plugin_music_time_range: short
          plugin_music_top_type: tracks
          plugin_music_user: .user.login
          plugin_people: yes
          plugin_people_limit: 24
          plugin_people_size: 28
          plugin_people_types: followers, following
          plugin_reactions: yes
          plugin_reactions_display: absolute
          plugin_reactions_limit: 200
          plugin_reactions_limit_discussions: 100
          plugin_reactions_limit_discussions_comments: 100
          plugin_reactions_limit_issues: 100
          plugin_skyline: yes
          plugin_skyline_frames: 60
          plugin_skyline_quality: 0.5
          plugin_skyline_settings: {
  "url": "https://skyline.github.com/${login}/${year}",
  "ready": "[...document.querySelectorAll('span')].map(span => span.innerText).includes('Share on Twitter')",
  "wait": 1,
  "hide": "button, footer, a"
}

          plugin_skyline_year: current-year
          plugin_stargazers: yes
          plugin_stargazers_charts: yes
          plugin_stargazers_charts_type: classic
          plugin_stargazers_worldmap: yes
          plugin_tweets: yes
          plugin_tweets_limit: 2
          plugin_tweets_user: nanzhi27

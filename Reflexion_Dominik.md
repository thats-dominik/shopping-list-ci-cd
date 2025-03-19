# Reflexion zur CI/CD-Pipeline

## 1. Struktur der Pipeline
- Die Pipeline besteht aus mehreren **Jobs**:
  - **Linting** prüft den Code-Style.
  - **Testing** führt Jest Tests aus.
  - **Build** erstellt die App.
  - **Deployment** simuliert den Upload.

## 2. Herausforderungen & Lösungen
- **Problem:** `npm test` funktionierte nicht, weil `jest-environment-jsdom` nicht installiert war.
  - **Lösung:** Installation mit `--legacy-peer-deps` erzwungen.
- **Problem:** `npm test` wurde im Actions nicht erkannt.
  - **Lösung:** Jest-Config (`jest.config.js`) angepasst.
- **Optimierung:** Durch **Job-Abhängigkeiten (`needs:`)** läuft die Pipeline besser & schneller.

## 3. Verbesserungsvorschläge
- **Caching für `node_modules` hinzufügen**, um Build-Zeit zu sparen.
- **Echtes Deployment** statt nur `echo "Deployment successful"`.
- **Mehr Tests für wichtige Funktionen schreiben**.

## Fazit
Die Pipeline sorgt für **automatische Quali Prüfung, Tests und Build**, bevor Code deployed wird.  
Für echte Produktion könnte ein **CD-Job mit Vercel o/ Docker** ergänzt werden.

## Autor
Dominik Hämmerle :)
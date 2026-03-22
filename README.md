# Przewidywanie Cen Nieruchomości (Boston House Prices)

## Opis Projektu
Projekt z dziedziny Machine Learningu polegający na budowie modelu sztucznej inteligencji, który przewiduje medianę cen mieszkań (w tysiącach dolarów) na podstawie cech demograficznych, geograficznych i infrastrukturalnych danej dzielnicy. 

Celem projektu było samodzielne przejście przez pełen cykl życia modelu ML (End-to-End): od załadowania i oczyszczenia danych, przez eksploracyjną analizę danych (EDA), aż po trening, ewaluację i eksport gotowych algorytmów.

## Wykorzystane Biblioteki Pythona
* **Analiza i obróbka danych:** Pandas, NumPy
* **Machine Learning:** Scikit-Learn (Linear Regression, Random Forest Regressor)
* **Wizualizacja danych:** Matplotlib, Seaborn
* **Eksport modelu:** Joblib

## 📊 Dane i Etyka w AI
W projekcie wykorzystano historyczny zbiór danych *Boston Housing Dataset*. 

**Ważna uwaga etyczna:** Zbiór ten oryginalnie zawierał kontrowersyjną zmienną demograficzną (`B` - wskaźnik oparty na rasie mieszkańców). Uznałem że nie powinno mieć to wpływu na wyniki mojego algorytmu, kolumna ta została celowo usunięta na etapie czyszczenia danych (Data Preprocessing).

## Modele i Wyniki
Zbiór danych został podzielony na część treningową (80%) i testową (20%). Przetestowałem dwa podejścia, a do oceny ich skuteczności użyłem metryki **MAE (Mean Absolute Error)**:

1. **Regresja Liniowa (Linear Regression)**
   * Algorytm bazowy (Baseline).
   * Pozwolił na łatwą interpretację wpływu poszczególnych cech na cenę (np. spadek ceny przy wyższej przestępczości).
   * **Błąd MAE:** ~3.11 tys. $

2. **Las Losowy (Random Forest Regressor)**
   * Bardziej zaawansowany algorytm zespołowy, radzący sobie z nieliniowymi zależnościami, szukający cech które najbardziej dzielą zbiór danych.
   * **Błąd MAE:** ~2.09 tys. $ (znacząca poprawa względem modelu bazowego).

## Struktura Repozytorium
* `house_prices_prediction.ipynb` - Główny notatnik z pełnym kodem, analizą i wykresami.
* `model_cen_mieszkan.pkl` - Wyeksportowany, wytrenowany model Lasu Losowego gotowy do użycia.
* `README.md` - Dokumentacja projektu.

## Jak wczytać model?
Gotowy model można wczytać w dowolnej aplikacji (np. Streamlit lub Flask) za pomocą biblioteki `joblib`:
```python
import joblib

# Wczytanie zamrożonego modelu
wczytany_model = joblib.load('model_cen_mieszkan.pkl')

# Przykładowa predykcja (gdzie 'nowe_dane' to odpowiednio sformatowana tabela z cechami nowej dzielnicy)
# przewidywana_cena = wczytany_model.predict(nowe_dane)

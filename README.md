# Valores_restricao_migracao
Teste simples de retorno de valores de limite em C#

using System;

class Program
{
    static void Main()
    {
        Console.WriteLine("Qual é o valor do cliente?");

        if (int.TryParse(Console.ReadLine(), out int valorLimite))
        {
            Console.WriteLine("O cliente tem restrição? (s/n)");

            string resposta = Console.ReadLine();

            if (resposta.Equals("s", StringComparison.OrdinalIgnoreCase))
            {
                valorLimite = Math.Min(valorLimite, 800); //se o valor for menor de 800, será validado o valor enviado
            }
            else if (resposta.Equals("n", StringComparison.OrdinalIgnoreCase))
            {
                
                valorLimite = Math.Min(valorLimite, 1500); // Se não houver restrição, e o valor inserido for a mais do limite de 1500, será considerado 500
            }
            else
            {
                Console.WriteLine("Resposta inválida. Use 's' ou 'n'.");
                return; // Sai do programa se a resposta for inválida.
            }

            int rotativo = (int)(valorLimite * 0.40);
            int exclusivo = (int)(valorLimite * 0.60);

            Console.WriteLine($"Limite rotativo: {rotativo} e Limite exclusivo: {exclusivo}");
        }
        else
        {
            Console.WriteLine("Erro, não foi possivel validar limites.");
        }
    }
}

